# Threat Modeling

## What Gets Skipped When Teams Are Moving Fast

In 2013, attackers installed malware on Target's point-of-sale terminals during the holiday shopping season. Forty million credit card numbers were stolen. The entry point was not a sophisticated zero-day exploit. It was credentials stolen from a third-party HVAC vendor that had network access to Target's systems.

A basic threat modeling exercise on the network architecture would have raised a question: why does an HVAC vendor need network connectivity that can reach payment terminals? That connectivity should never have existed. The design had a trust boundary problem that nobody stopped to examine before the system went live.

Threat modeling is the practice of systematically asking "what could go wrong?" before code is written and systems are deployed. It is not about predicting every possible attack. It is about finding the design-level problems that are cheap to fix before implementation and catastrophically expensive to fix after a breach.[1]

The reason teams skip it is the same reason teams skip documentation, security requirements, and code review: pressure. There is always a deadline. There is always a feature backlog. Threat modeling feels like overhead when you are trying to ship.

The counterargument is simple: Target spent $200 million in the first year responding to the breach. The threat model session that would have caught the HVAC vendor connectivity issue would have taken two hours.

---

## The Four Questions

Adam Shostack, who led threat modeling at Microsoft and wrote the field's most comprehensive book on the subject, reduces threat modeling to four questions:[2]

1. **What are we building?** Understand the system well enough to reason about it.
2. **What can go wrong?** Identify threats to the system.
3. **What are we going to do about it?** Define mitigations for each threat.
4. **Did we do a good enough job?** Verify that the process was complete and mitigations are effective.

These questions apply regardless of which methodology you use. The methodologies are structured ways of answering question 2 more systematically.

---

## Step 1: Understand What You Are Building

Threat modeling starts with a model: a representation of the system that is detailed enough to reason about security without being so detailed that it takes weeks to produce.

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

{% hint style="success" %}
**A worked example: STRIDE on a login flow.** Take the simplest possible system — a user logging into a web app that checks credentials against a database:

```
[User Browser] --(1) HTTPS login--> [Web App] --(2) SQL lookup--> [Credentials DB]
   external          | trust boundary           internal
```

Walk the elements and ask the six questions where they apply. A realistic first pass:

| # | Element / Flow | STRIDE threat | Concrete risk | Mitigation |
|---|---|---|---|---|
| 1 | Login flow (1) | **S**poofing | Attacker brute-forces or credential-stuffs the login | Rate limiting, account lockout, MFA |
| 2 | Login flow (1) | **T**ampering | Attacker on the network alters the request | TLS 1.3 (already on the HTTPS flow) |
| 3 | Web App | **I**nfo disclosure | Login error reveals whether the username exists | Generic "invalid credentials" message |
| 4 | SQL lookup (2) | **T**ampering | Unparameterized query allows SQL injection | Parameterized queries / prepared statements |
| 5 | Credentials DB | **I**nfo disclosure | DB stores passwords in plaintext or fast hashes | Argon2id password hashing (see Chapter 7) |
| 6 | Web App | **R**epudiation | No record of who logged in or tried to | Authentication audit logging |
| 7 | Login flow (1) | **D**enial of service | Login endpoint flooded, locking out real users | Rate limiting + CAPTCHA on repeated failures |
| 8 | Web App | **E**levation of privilege | Session token doesn't bind to user role; user reaches admin functions | Server-side authorization checks, deny by default |

Eight concrete, fixable findings from a two-box diagram — most of which map directly to OWASP Top 10 categories. Notice how the same control (rate limiting, TLS) often answers more than one threat, and how the diagram, not cleverness, is what made the threats discoverable. Then the critical last step: each row becomes a ticket in the issue tracker with an owner, or the exercise was theater.
{% endhint %}

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

**A concrete ATT&CK workflow** (the equivalent of the STRIDE walkthrough above, for defenders):

1. **Scope to your environment.** Don't try to cover all 14 tactics at once. Pick the techniques that match your actual stack — internet-facing web app, Windows AD, cloud, etc. Open ATT&CK Navigator and start a fresh layer.
2. **Prioritize with real-world data.** Not all techniques are equally likely. Cross-reference against threat intelligence: which techniques are the groups targeting *your industry* actually using? The CISA Known Exploited Vulnerabilities (KEV) catalog and ATT&CK's own group pages tell you what's live, not just theoretically possible.
3. **Score your coverage per technique.** For each in-scope technique, mark whether you can *prevent* it, *detect* it, or neither. Color the Navigator layer accordingly. Red cells are your gaps.
4. **Drive work from the gaps.** A technique you can neither prevent nor detect (say, T1003 credential dumping) becomes a detection-engineering or hardening backlog item.

Where STRIDE asks "what could go wrong with this design?", ATT&CK asks "can we stop and see what real attackers do?" Mature teams use both: STRIDE during design, ATT&CK to measure detection coverage of the running system.

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

OCTAVE, developed by Carnegie Mellon's SEI, takes an organizational rather than system-level view. It focuses on identifying mission-critical assets, the threats to those assets, and organizational vulnerabilities, including people and process weaknesses, not just technical ones.[8]

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

### Continuous Threat Modeling

The "threat model once, before launch" approach made sense when software shipped a few times a year. Modern teams deploy daily, and a threat model that's accurate at launch is stale within a sprint. The response is **continuous threat modeling**: small, ongoing increments instead of a single heavyweight exercise.

- **Threat model the change, not the whole system.** When a feature adds a new data flow across a trust boundary — a new third-party API, a new file upload, a new admin endpoint — model *that*, in minutes, during design.
- **Make it part of the definition of done.** A lightweight checklist on the pull request ("does this add a trust boundary? touch auth? handle untrusted input?") catches most of what matters without a meeting.
- **Keep the model in version control.** Threat-modeling-as-code tools (pytm, Threagile) let the model live next to the code and update with it, so the diagram never drifts from reality — the single most common way threat models become useless.

### Threat Modeling the Supply Chain

The Target breach that opened this chapter was a supply-chain attack, and they've only grown since — SolarWinds (2020), the 3CX compromise (2023), the XZ Utils backdoor (2024). Yet most threat models stop at the system boundary and treat dependencies as trusted. They shouldn't.

When you threat model, treat each third-party component as an untrusted external entity with a data flow into your system, and ask: What access does this dependency have? What happens if *it* is compromised — a malicious package update, a breached vendor, a poisoned build pipeline? Could a backdoored library exfiltrate data or escalate privilege? This reframing turns "we use library X" into a flow that crosses a trust boundary and gets the same STRIDE scrutiny as any other. The concrete defenses — SBOMs, dependency pinning, build provenance — live in Chapters 10 and 11; the threat-modeling job is to make the supply chain *visible* in the model in the first place.

---

## Try This

1. **Threat model something you use.** Draw a two-or-three-box data flow diagram of a simple app — a to-do app, a login page, a contact form. Mark the trust boundary. Then run STRIDE down every element exactly like the worked login example above, and write at least five findings with a mitigation each. Do it on paper or a whiteboard; the diagram doesn't need to be pretty.
2. **Do it in code.** Install [pytm](https://github.com/OWASP/pytm) and adapt the example in this chapter to your diagram from exercise 1. Run `tm.process()` and read the generated threat report. Seeing threats fall out of a code definition is the "aha" that makes threat-modeling-as-code click — and the script is portfolio material.
3. **Map coverage with ATT&CK.** Open the free [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/), pick five techniques relevant to a web app (start with T1190 and T1110), and honestly mark whether you could detect each. Your red cells are exactly what a detection engineer gets paid to fix.

---

## Key Takeaways

- Threat modeling is asking "what could go wrong?" at design time, when fixes are cheap. Target's $200M breach traced to a trust-boundary question that a two-hour session would have raised.
- Shostack's four questions — what are we building, what can go wrong, what will we do about it, did we do a good job — structure every methodology.
- The diagram does the work: data flow diagrams with explicit trust boundaries make threats discoverable. Every flow crossing a boundary is attack surface.
- Match the method to the job: STRIDE for systematic design analysis, ATT&CK for measuring detection coverage, attack trees for explaining a specific goal, PASTA/OCTAVE for business- and org-level risk.
- A threat model is only real if its findings become tracked tickets — and only stays real if it's continuous, kept in version control, and extended to the supply chain.

---

## References

[1] Shostack, A. (2014). *Threat Modeling: Designing for Security*. Wiley. ISBN 978-1-118-80999-0.

[2] Shostack, A. (2014). *Threat Modeling: Designing for Security*. Wiley. ISBN 978-1-118-80999-0. (Chapter 1: Diving In)

[3] Kohnfelder, L., & Garg, P. (1999). *The Threats to Our Products*. Microsoft Interface. Microsoft Corporation. Retrieved from https://adam.shostack.org/microsoft/The-Threats-To-Our-Products.docx

[4] MITRE Corporation. (2024). *MITRE ATT&CK Framework*. Retrieved from https://attack.mitre.org

[5] MITRE Corporation. (2024). *ATT&CK Navigator*. GitHub. Retrieved from https://mitre-attack.github.io/attack-navigator/

[6] Schneier, B. (1999). Attack trees: Modeling security threats. *Dr. Dobb's Journal*, 24(12), 21-29. Retrieved from https://www.schneier.com/academic/archives/1999/12/attack_trees.html

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

*Questions about threat modeling methodologies, running your first session, or tool selection? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back. This book is open source and your additions are welcome.*
