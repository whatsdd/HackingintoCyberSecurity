# Threat Modeling

## What Gets Skipped When Teams Are Moving Fast

In 2013, attackers installed malware on Target's point-of-sale terminals during the holiday shopping season. Forty million credit card numbers were stolen. The entry point was not a sophisticated zero-day exploit -- it was credentials stolen from a third-party HVAC vendor that had network access to Target's systems.

A basic threat modeling exercise on the network architecture would have raised a question: why does an HVAC vendor need network connectivity that can reach payment terminals? That connectivity should never have existed. The design had a trust boundary problem that nobody stopped to examine before the system went live.

Threat modeling is the practice of systematically asking "what could go wrong?" before code is written and systems are deployed. It is not about predicting every possible attack. It is about finding the design-level problems that are cheap to fix before implementation and catastrophically expensive to fix after a breach.[1]

The reason teams skip it is the same reason teams skip documentation, security requirements, and code review: pressure. There is always a deadline. There is always a feature backlog. Threat modeling feels like overhead when you are trying to ship.

The counterargument is simple: Target spent $200 million in the first year responding to the breach. The threat model session that would have caught the HVAC vendor connectivity issue would have taken two hours.

---

## The Four Questions

Adam Shostack, who led threat modeling at Microsoft and wrote the field's most comprehensive book on the subject, reduces threat modeling to four questions:[2]

1. **What are we building?** -- Understand the system well enough to reason about it
2. **What can go wrong?** -- Identify threats to the system
3. **What are we going to do about it?** -- Define mitigations for each threat
4. **Did we do a good enough job?** -- Verify that the process was complete and mitigations are effective

These questions apply regardless of which methodology you use. The methodologies are structured ways of answering question 2 more systematically.

---

## Step 1: Understand What You Are Building

Threat modeling starts with a model -- a representation of the system that is detailed enough to reason about security without being so detailed that it takes weeks to produce.

**Data Flow Diagrams (DFDs)** are the standard artifact. A DFD shows:

- **Processes**: Systems, applications, or components that transform data (drawn as circles or rounded rectangles)
- **Data stores**: Databases, files, caches where data lives (drawn as parallel lines)
- **External entities**: Users, third-party systems, or other things outside your control boundary (drawn as rectangles)
- **Data flows**: Arrows showing data moving between components, labeled with what the data is
- **Trust boundaries**: Lines separating zones of different trust levels (typically dashed lines)

```
[User Browser] --HTTPS--> [Web Server] --SQL--> [Database]
               external       DMZ          internal
               |_______________|_______________|
               Trust boundary at DMZ edge
```

Trust boundaries are where the threat model earns its value. Every data flow that crosses a trust boundary is a potential attack surface. Data entering from an external entity is untrusted. Data passing from a lower-trust zone to a higher-trust zone requires special scrutiny.

{% hint style="info" %}
**Practical tip:** Start with a simple diagram. A whiteboard photo works. A perfectly formatted diagram produced after three meetings does not. The goal is to get the team thinking about data flows and trust boundaries, not to produce a deliverable.

For every arrow on your diagram, ask: who controls this data? What happens if it is malicious? What happens if the connection is intercepted? The questions are more valuable than the diagram itself.
{% endhint %}

---

## Step 2: Identify Threats

### STRIDE

STRIDE is the most widely used threat categorization framework. Developed at Microsoft by Loren Kohnfelder and Praerit Garg in 1999, it provides a checklist of six threat categories applied systematically to each element in the DFD.[3]

| Threat | Property Violated | Applied To | Example |
|---|---|---|---|
| **Spoofing** | Authentication | Processes, external entities | Attacker impersonates a user by forging JWT tokens |
| **Tampering** | Integrity | Data flows, data stores, processes | Attacker modifies API responses via MitM attack |
| **Repudiation** | Non-repudiation | Processes, external entities | User denies placing a fraudulent order; no audit log exists |
| **Information Disclosure** | Confidentiality | All elements | Error messages expose stack traces with internal paths and versions |
| **Denial of Service** | Availability | Processes, data stores | Attacker floods login endpoint; no rate limiting; server exhausted |
| **Elevation of Privilege** | Authorization | Processes | Regular user accesses admin API endpoint by manipulating user ID in request |

**How to apply STRIDE:**

For each element in your DFD, work through all six threat categories. For each combination of (element type, threat category), ask whether that threat is possible and what its impact would be.

Not every STRIDE category applies to every element type:

| Element | S | T | R | I | D | E |
|---|---|---|---|---|---|---|
| External Entity | yes | -- | yes | -- | -- | -- |
| Process | yes | yes | yes | yes | yes | yes |
| Data Store | -- | yes | yes | yes | yes | -- |
| Data Flow | -- | yes | -- | yes | yes | -- |

Running STRIDE on a system with five processes, three data stores, and four data flows produces a structured list of candidate threats. Most will be low-severity or already mitigated. The ones that are not are your findings.

### MITRE ATT&CK

MITRE ATT&CK is a knowledge base of adversary tactics, techniques, and procedures (TTPs) based on observed real-world attacks. Where STRIDE provides categories for reasoning about what could go wrong, ATT&CK provides a catalog of what attackers actually do.[4]

ATT&CK is organized into 14 tactics (the "why" of an attack) with hundreds of techniques and sub-techniques (the "how"):

| Tactic | What It Represents |
|---|---|
| Reconnaissance | Information gathering before the attack |
| Resource Development | Establishing infrastructure, accounts, tooling |
| Initial Access | Getting a foothold (phishing, exploit, supply chain) |
| Execution | Running attacker-controlled code |
| Persistence | Maintaining access across reboots and credentials changes |
| Privilege Escalation | Gaining higher permissions |
| Defense Evasion | Avoiding detection |
| Credential Access | Stealing credentials |
| Discovery | Learning about the environment |
| Lateral Movement | Moving through the network |
| Collection | Gathering target data |
| Command and Control | Communicating with compromised systems |
| Exfiltration | Stealing data out |
| Impact | Disrupting, destroying, encrypting, or manipulating data |

**Using ATT&CK for threat modeling:**

For a given system, identify which ATT&CK techniques are relevant. If your system has internet-facing web applications, phishing (T1566) and exploitation of public-facing applications (T1190) are relevant initial access techniques. If your system runs Windows in a domain environment, credential dumping (T1003) and lateral movement via SMB/Pass-the-Hash are relevant.

The ATT&CK Navigator tool allows teams to visually map relevant techniques onto the ATT&CK matrix and document which detections and mitigations are in place for each. This produces a heat map of coverage that makes gaps immediately visible.[5]

### Attack Trees

Attack trees, introduced by Bruce Schneier in 1999, represent attacks as tree structures where the root node is the attacker's goal and child nodes are the methods to achieve it.[6]

```
Root: Steal customer payment data
├── Attack database directly
│   ├── Exploit SQL injection in web app
│   └── Gain DBA credentials (phishing, brute force)
├── Intercept traffic
│   ├── Downgrade HTTPS connection
│   └── Compromise SSL certificate
└── Compromise insider
    ├── Phish employee with database access
    └── Bribe or coerce employee
```

Attack trees excel at exploring the attack space for a specific goal. They naturally decompose complex attacks into atomic steps and make it easy to assign likelihood and cost to each leaf node. They are less systematic than STRIDE (which ensures all threat categories are considered) but more intuitive for explaining threats to non-technical stakeholders.

### PASTA (Process for Attack Simulation and Threat Analysis)

PASTA is a seven-stage, risk-centric framework designed to align threat modeling with business objectives. Its stages move from business impact analysis through technical decomposition to attack enumeration and risk scoring.[7]

| Stage | Activity |
|---|---|
| 1. Define Objectives | Identify business and security objectives; define risk appetite |
| 2. Define Technical Scope | System components, dependencies, technologies in scope |
| 3. Application Decomposition | DFDs, use cases, trust boundaries |
| 4. Threat Analysis | Threat intelligence, threat actor profiles, attack scenarios |
| 5. Vulnerability Analysis | Known CVEs, design weaknesses, misconfigurations |
| 6. Attack Modeling | Attack trees, attack simulation against identified vulnerabilities |
| 7. Risk and Impact Analysis | Risk scoring, remediation prioritization |

PASTA is more resource-intensive than STRIDE and requires broader stakeholder involvement. It is most appropriate for high-value systems where a business-aligned risk analysis is worth the investment.

### OCTAVE (Operationally Critical Threat, Asset, and Vulnerability Evaluation)

OCTAVE, developed by Carnegie Mellon's SEI, takes an organizational rather than system-level view. It focuses on identifying mission-critical assets, the threats to those assets, and organizational vulnerabilities -- including people and process weaknesses -- not just technical ones.[8]

OCTAVE is particularly appropriate for enterprise risk assessments and for organizations that need to understand systemic risk rather than application-level threats.

---

## Step 3: Mitigate Threats

For each identified threat, one of four responses applies:

| Response | When to Use |
|---|---|
| **Mitigate** | Implement a control that reduces the likelihood or impact |
| **Eliminate** | Change the design to remove the threat entirely (best option when possible) |
| **Transfer** | Shift risk to a third party (e.g., use a managed auth service rather than building your own) |
| **Accept** | Acknowledge the risk and document the decision with a rationale |

**Mitigation mapping to STRIDE:**

| Threat | Primary Mitigations |
|---|---|
| Spoofing | Authentication (MFA, strong session management, certificate pinning) |
| Tampering | Integrity checks (digital signatures, HMAC, parameterized queries, input validation) |
| Repudiation | Audit logging with tamper-evident storage |
| Information Disclosure | Encryption (TLS in transit, AES at rest), access controls, minimal error disclosure |
| Denial of Service | Rate limiting, input size limits, auto-scaling, CDN and DDoS mitigation |
| Elevation of Privilege | Authorization enforcement (deny by default), principle of least privilege |

---

## Step 4: Verify

Threat model verification asks whether the process was complete and whether mitigations are effective.

**Completeness checks:**
- Does the DFD match the actual implemented system? (Threat models built on outdated diagrams are useless)
- Are all trust boundaries identified?
- Are all STRIDE categories applied to all relevant elements?
- Are all high-severity threats assigned a mitigation?

**Effectiveness checks:**
- Are mitigations implemented (not just planned)?
- Do security tests verify that mitigations work?
- Are there test cases for each identified threat?

Integrating threat model findings into the issue tracker ensures that identified threats become tracked engineering work, not documents that accumulate in a security team's drive.

---

## Threat Modeling Tools

| Tool | Type | Notes |
|---|---|---|
| **Microsoft Threat Modeling Tool** | Desktop application | Free; native STRIDE support; SDL-aligned; Windows only |
| **OWASP Threat Dragon** | Web/desktop (open-source) | Cross-platform; DFD-based; GitHub integration |
| **IriusRisk** | Commercial platform | Automated threat generation from architecture diagrams; enterprise-grade |
| **Pytm** | Python library | Code-first threat modeling; generates DFDs and threats from Python definitions |
| **Threagile** | Open-source (YAML-based) | Threat modeling as code; CI/CD integration |

```python
# Example: Pytm threat model in code
from pytm import TM, Server, Datastore, Dataflow, Boundary, Actor

tm = TM("E-commerce Platform")

internet = Boundary("Internet")
dmz = Boundary("DMZ")
internal = Boundary("Internal")

user = Actor("Customer", inBoundary=internet)
web = Server("Web Application", inBoundary=dmz)
db = Datastore("Customer Database", inBoundary=internal)

Dataflow(user, web, "HTTPS Request")
Dataflow(web, db, "SQL Query")

tm.process()  # Generates threats, DFD, and report
```

Threat modeling as code (pytm, Threagile) enables threat models to live in version control alongside the code they describe, and to be automatically updated when the system changes.

---

## When to Threat Model

Threat modeling is most valuable during design. It loses value as implementation progresses, because the cost of design changes rises with every line of code written.

| Trigger | What to Threat Model |
|---|---|
| New feature or system | Full threat model before implementation begins |
| Significant architecture change | Update existing threat model for affected components |
| New third-party integration | Trust boundary analysis for the integration point |
| Post-incident review | Verify threat model against observed attack technique |
| Annual security review | Validate that threat model reflects the current system |

A threat model produced once and never updated is a historical document. Systems change. Threat landscapes change. The threat model should change with them.

---

## References

[1] Shostack, A. (2014). *Threat Modeling: Designing for Security*. Wiley. ISBN 978-1-118-80999-0.

[2] Shostack, A. (2014). *Threat Modeling: Designing for Security*. Wiley. ISBN 978-1-118-80999-0. (Chapter 1: Diving In)

[3] Kohnfelder, L., & Garg, P. (1999). *The Threats to Our Products*. Microsoft Interface. Microsoft Corporation. Retrieved from https://adam.shostack.org/microsoft/The-Threats-To-Our-Products.docx

[4] MITRE Corporation. (2024). *MITRE ATT&CK Framework*. Retrieved from https://attack.mitre.org

[5] MITRE Corporation. (2024). *ATT&CK Navigator*. GitHub. Retrieved from https://mitre-attack.github.io/attack-navigator/

[6] Schneier, B. (1999). Attack trees: Modeling security threats. *Dr. Dobb's Journal*, 24(12), 21--29. Retrieved from https://www.schneier.com/academic/archives/1999/12/attack_trees.html

[7] UCSan Diego and VerSprite. (2012). *PASTA: Process for Attack Simulation and Threat Analysis*. VerSprite Security Research. Retrieved from https://versprite.com/blog/what-is-pasta-threat-modeling/

[8] Alberts, C., Dorofee, A., Stevens, J., & Woody, C. (2003). *Introduction to the OCTAVE Approach*. Carnegie Mellon University Software Engineering Institute. Retrieved from https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=51546

---

## Further Reading

| Resource | What It Covers |
|---|---|
| Shostack, *Threat Modeling: Designing for Security* (Wiley, 2014) | The definitive book on threat modeling; covers all major methodologies and practical application |
| [OWASP Threat Modeling Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html) | Concise practical reference; good starting point for running first sessions |
| [MITRE ATT&CK](https://attack.mitre.org) | The definitive catalog of adversary TTPs; essential reference for threat identification |
| [Threat Dragon](https://owasp.org/www-project-threat-dragon/) | Free, open-source threat modeling tool from OWASP |
| [Pytm](https://github.com/OWASP/pytm) | Threat modeling as code; integrates with CI/CD pipelines |

---

*Questions about threat modeling methodologies, running your first session, or tool selection? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back -- this book is open source and your additions are welcome.*
