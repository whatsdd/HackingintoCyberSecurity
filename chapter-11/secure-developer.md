# Secure Developer: Building Security In

## The Most Expensive Way to Find a Bug

In 2017, Equifax's engineering team was using Apache Struts. Apache Struts had a critical remote code execution vulnerability -- CVE-2017-5638. A patch was released in March. Equifax's systems were exploited in May. 147 million people's data was exposed.

The patch existed. The process to apply it did not work. But trace that further back: the vulnerability itself existed because software was shipped without adequate security review of how user input was handled. A fundamental secure coding principle -- validate and sanitize all untrusted input -- was not applied in a component that hundreds of thousands of applications would eventually depend on.

Security vulnerabilities are primarily software defects. And like all software defects, they are dramatically cheaper to fix when found early. NIST research on software defect costs shows that a bug found during the requirements phase costs roughly one unit to fix. The same bug found in production costs 30 times more. Found after a breach, the costs in legal fees, regulatory fines, remediation, and reputational damage multiply that by another order of magnitude.[1]

The Secure Software Development Lifecycle (SSDLC) is the discipline of building security into every phase of software development -- requirements, design, implementation, testing, and deployment -- rather than attempting to add it after the fact.

---

## Why Developers Need to Own Security

For most of software history, security was someone else's problem. Developers wrote features. Security teams reviewed them before release, or after a breach. The gap between those roles produced systems that were functionally correct and security-broken simultaneously.

That model is obsolete. Modern development teams deploy continuously, sometimes dozens of times per day. There is no "before release" gate that a security team can man at that velocity. Security has to be in the hands of the people writing the code.

This does not mean every developer needs to be a penetration tester. It means every developer needs to know:

- The common vulnerability classes in the languages and frameworks they use
- How to avoid introducing those vulnerabilities in new code
- How to recognize them in code review
- How to use the security tools in the CI/CD pipeline
- Who to escalate to when they are unsure

The investment in developer security training pays back measurably. Google's Project Zero data shows that most high-severity vulnerabilities exploited in the wild fall into a small number of recurring categories -- categories that developers who have received targeted training reliably avoid.[2]

---

## SSDLC Models

Several frameworks formalize the integration of security into the development lifecycle.

### Microsoft Security Development Lifecycle (SDL)

The Microsoft SDL was developed in response to the Windows XP security crisis of the early 2000s -- a period when Microsoft products were so widely exploited that the company's reputation was seriously threatened. Bill Gates' 2002 "Trustworthy Computing" memo redirected the entire company toward security, and SDL was the operational result.[3]

Microsoft SDL defines security activities across phases:

| Phase | Security Activity |
|---|---|
| Training | Annual security training for all developers |
| Requirements | Define security requirements; abuse cases; privacy requirements |
| Design | Attack surface analysis; threat modeling |
| Implementation | Use approved tools and libraries; deprecate unsafe functions; static analysis |
| Verification | Dynamic analysis; fuzz testing; attack surface review |
| Release | Incident response plan; final security review |
| Response | Incident response execution; security update process |

Microsoft publishes SDL documentation freely and has opened portions of the process as guidance applicable to any organization.

### OWASP Software Assurance Maturity Model (SAMM)

OWASP SAMM provides a measurable framework for assessing and improving a software security program across five business functions: Governance, Design, Implementation, Verification, and Operations. Each function has three practices, and each practice has three maturity levels.[4]

SAMM is useful because it describes where you are and where you could be, rather than prescribing a single path. An organization at SAMM maturity level 1 (basic hygiene) has a realistic path to level 2 (defined processes) without needing to implement everything at once.

### BSIMM (Building Security In Maturity Model)

BSIMM differs from SDL and SAMM in that it is descriptive rather than prescriptive. It is based on observational data from security programs at real organizations, measuring what they actually do rather than what frameworks say they should do.[5] BSIMM data is useful for benchmarking -- understanding how your security program compares to peers in your industry.

---

## Phase 1: Security Requirements

Security requirements are the security properties a system must have. They are defined before design begins, not discovered during testing.

**Types of security requirements:**

- **Functional security requirements**: Specific behaviors the system must implement (MFA for administrator access, AES-256 encryption for stored credentials, session timeout after 15 minutes of inactivity)
- **Non-functional security requirements**: Properties the system must exhibit (audit logging of all authentication events, response to security scan findings within defined SLAs)
- **Compliance requirements**: Security behaviors mandated by regulation (GDPR data minimization, HIPAA audit controls, PCI-DSS encryption of cardholder data)
- **Abuse cases**: Descriptions of how an attacker might try to misuse the system -- the security complement to use cases

{% hint style="info" %}
**Abuse cases are underused.** A use case describes what a legitimate user does. An abuse case describes what a malicious user attempts. For a login function, the use case is "user enters valid credentials and is authenticated." Abuse cases include "attacker attempts to brute-force credentials," "attacker attempts SQL injection in the username field," "attacker replays an expired session token."

Writing abuse cases forces developers to think about the attacker's perspective before design is finalized -- which is exactly when it is cheapest to prevent the corresponding vulnerability.
{% endhint %}

---

## Phase 2: Threat Modeling

Threat modeling is the systematic process of identifying what can go wrong in a system, why it can go wrong, and what to do about it. It is performed during the design phase, on diagrams of the system architecture before implementation, when changing designs is cheap.

The output of threat modeling is a prioritized list of threats and corresponding mitigations -- design-level security requirements that feed back into the engineering work.

### The STRIDE Model

STRIDE is the most widely used threat categorization framework, developed at Microsoft. For each component and data flow in a system, the analyst asks whether six types of threat are possible:[6]

| Threat | Property Violated | Example |
|---|---|---|
| **Spoofing** | Authentication | Attacker impersonates another user by forging identity tokens |
| **Tampering** | Integrity | Attacker modifies data in transit or at rest |
| **Repudiation** | Non-repudiation | User denies having performed an action; no audit log exists to prove otherwise |
| **Information Disclosure** | Confidentiality | Sensitive data exposed through error messages, misconfigured storage, or side channels |
| **Denial of Service** | Availability | Attacker exhausts resources, making the system unavailable to legitimate users |
| **Elevation of Privilege** | Authorization | Attacker gains higher permissions than intended |

### How to Threat Model

1. **Define scope**: What are we modeling? (A specific feature, an API, an entire system)
2. **Decompose the system**: Draw a Data Flow Diagram (DFD) showing components, data stores, data flows, and trust boundaries
3. **Identify threats**: For each element in the DFD, apply STRIDE to generate candidate threats
4. **Rate threats**: Use DREAD or a risk matrix to prioritize (likelihood × impact)
5. **Define mitigations**: For each rated threat, specify the control that addresses it
6. **Validate**: Ensure mitigations are implemented and verify they address the threat

{% hint style="success" %}
**Practical tip:** Threat modeling does not require a specialist or a two-day workshop. A one-hour whiteboard session with a developer, architect, and someone familiar with attack techniques -- using a simple diagram and the STRIDE mnemonic as a checklist -- produces actionable findings that a purely technical code review will miss.

The question "what could go wrong if an attacker controls this input?" asked during design prevents far more vulnerabilities than the same question asked during a post-release penetration test.
{% endhint %}

---

## Phase 3: Secure Coding Principles

These principles apply across languages, frameworks, and domains. They are not a complete substitute for knowing the specific vulnerability classes relevant to your stack, but they are the foundation.

### Validate All Input

Every piece of data entering your system from outside your control is untrusted. This includes user input, API responses, file contents, database query results, environment variables, and headers.

- Validate input against a strict allowlist of acceptable values (not a denylist of bad values -- attackers will find what you missed)
- Reject or sanitize input that does not conform
- Never trust data from the client side, even if your client-side code validates it first

### Encode All Output

When data is output to another context -- a web page, a database query, a command line, a log file -- it must be encoded for that context to prevent injection. A string safe for display in HTML is not necessarily safe for inclusion in a JavaScript expression or a SQL query.

- Use context-specific output encoding: HTML encoding for HTML context, SQL parameterization for database queries, OS command escaping for shell commands
- Never build queries, commands, or markup through string concatenation with untrusted data

```python
# WRONG: SQL built through string concatenation
query = "SELECT * FROM users WHERE username = '" + username + "'"

# RIGHT: Parameterized query
query = "SELECT * FROM users WHERE username = %s"
cursor.execute(query, (username,))
```

### Principle of Least Privilege

Every component, service, and user account should operate with the minimum permissions necessary to perform its function. A web application that only reads from a database should not have write permissions. A service account that only calls one API should not have access to the entire API scope.

Least privilege limits blast radius: if a component is compromised, the attacker inherits only the permissions that component had -- not the permissions of everything else on the system.

### Fail Securely

When a system encounters an error, it should fail into a secure state. Failed authentication should result in access denied, not access granted. An exception in a security check should not default to allowing the operation.

Error messages shown to users should be generic ("An error occurred"). Detailed error information should be logged internally but never returned to the client, where it provides attackers with information about the system's internals.

### Defense in Depth

Do not rely on a single security control. Layer controls so that the failure of any one does not result in a compromise. Input validation + parameterized queries is more robust than either alone. MFA + session management + audit logging is more robust than any single authentication control.

### Secure Defaults

Systems should be secure out of the box without requiring administrators to take additional action. Insecure features should require explicit opt-in, not opt-out. Default passwords should not exist. Debug endpoints should be disabled by default in production builds.

---

## Phase 4: Dependency Management

Modern applications are 80 to 95% open-source code. Every dependency you include carries its own vulnerability history and future CVEs. Managing that risk is an ongoing development responsibility.

{% hint style="warning" %}
**Transitive dependencies are your responsibility too.** When you include a library, you implicitly include everything that library depends on. The Log4Shell vulnerability (CVE-2021-44228) was introduced into millions of applications not through direct use of Log4j, but through third-party libraries that used it internally. Organizations discovered they were vulnerable to a critical RCE flaw in code they had never knowingly chosen to include.[7]

Run SCA (Software Composition Analysis) tools -- Snyk, Dependabot, OWASP Dependency-Check -- as part of your build process. Know what you are shipping.
{% endhint %}

Dependency management best practices:

- Pin dependency versions exactly (not ranges) to ensure reproducible builds and control when you take updates
- Automate vulnerability scanning in the CI/CD pipeline
- Review dependencies before adding them: Does this library have a security track record? Is it actively maintained? What is its download source? (Supply chain attacks via typosquatting are real)
- Remove unused dependencies: every unused package is risk without benefit

---

## Phase 5: Security Testing

Security testing in the SSDLC is not a gate at the end. It is a continuous activity integrated into development.

| Testing Type | When | What It Finds |
|---|---|---|
| **Unit tests for security** | Development | Logic flaws, edge case handling, security function correctness |
| **SAST (Static Analysis)** | Commit / PR | Code-level vulnerability patterns, hardcoded secrets |
| **SCA (Dependency Scanning)** | Build | Known vulnerabilities in dependencies |
| **DAST (Dynamic Analysis)** | Test / Staging | Runtime vulnerabilities: injection, auth bypass, business logic |
| **Penetration testing** | Pre-release / periodic | Complex, chained vulnerabilities requiring human creativity |
| **Fuzzing** | Build / Periodic | Input handling flaws, crashes, unexpected behavior under malformed input |

**Fuzzing** deserves specific mention. Fuzzing (fuzz testing) involves sending large volumes of unexpected, malformed, or random inputs to a program to find crashes, hangs, and unexpected behavior that manual testing misses. Tools like AFL++, libFuzzer, and OSS-Fuzz (Google's free fuzzing infrastructure for open-source projects) have found thousands of critical vulnerabilities in widely used software that years of manual review missed.[8]

---

## Phase 6: Security Code Review

Code review is one of the most cost-effective security activities. A developer familiar with common vulnerability classes, reviewing their colleagues' code, catches issues before they reach testing infrastructure.

**What to look for in security-focused code review:**

- Input handling: Is all external input validated?
- Output encoding: Are outputs properly encoded for their destination context?
- Authentication and authorization: Are access controls consistently applied? Are there paths that skip checks?
- Cryptography: Are approved algorithms used? Are keys handled securely? Is there any homegrown crypto?
- Error handling: Do errors leak sensitive information? Do failures fail securely?
- Logging: Are security-relevant events logged? Is sensitive data excluded from logs?
- Dependencies: Are new dependencies necessary? Are they from trusted sources?

---

## OWASP Top 10 for Developers

The OWASP Top 10 is the most widely referenced categorization of critical web application security risks.[9] Every developer building web applications needs to understand these categories well enough to recognize and prevent them in their own code.

| Rank | Category | Prevent It By |
|---|---|---|
| A01 | Broken Access Control | Enforce authorization checks server-side; deny by default |
| A02 | Cryptographic Failures | Use TLS everywhere; encrypt sensitive data at rest; use modern algorithms |
| A03 | Injection | Parameterized queries; input validation; output encoding |
| A04 | Insecure Design | Threat modeling; abuse cases; security requirements before implementation |
| A05 | Security Misconfiguration | Secure defaults; IaC scanning; remove unnecessary features |
| A06 | Vulnerable Components | SCA scanning; dependency management; timely patching |
| A07 | Authentication Failures | MFA; secure password storage (bcrypt/Argon2); account lockout |
| A08 | Software and Data Integrity | Code signing; verify integrity of updates; CI/CD pipeline security |
| A09 | Security Logging Failures | Log authentication events, access failures, privilege changes |
| A10 | Server-Side Request Forgery | Validate and allowlist URLs; restrict outbound connections |

---

## References

[1] National Institute of Standards and Technology. (2002). *The Economic Impacts of Inadequate Infrastructure for Software Testing*. NIST Planning Report 02-3. doi:10.6028/NIST.IR.7007

[2] Google Project Zero. (2022). *0-day In-The-Wild Exploitation in 2022*. Google. Retrieved from https://googleprojectzero.blogspot.com/2023/07/the-root-cause-of-large-number-of.html

[3] Howard, M., & Lipner, S. (2006). *The Security Development Lifecycle: SDL: A Process for Developing Demonstrably More Secure Software*. Microsoft Press. ISBN 978-0-7356-2214-2.

[4] OWASP Foundation. (2020). *OWASP Software Assurance Maturity Model (SAMM) v2.0*. Open Web Application Security Project. Retrieved from https://owaspsamm.org/

[5] Synopsys. (2023). *Building Security In Maturity Model (BSIMM14)*. Synopsys. Retrieved from https://www.synopsys.com/software-integrity/resources/analyst-reports/bsimm.html

[6] Shostack, A. (2014). *Threat Modeling: Designing for Security*. Wiley. ISBN 978-1-118-80999-0.

[7] Khawaja, A. (2022). Log4Shell: The Log4j vulnerability emergency. *CISA Advisory*. Retrieved from https://www.cisa.gov/news-events/news/apache-log4j-vulnerability-guidance

[8] Serebryany, K. (2017). *OSS-Fuzz: Five months later, and rewarding projects*. Google Security Blog. Retrieved from https://security.googleblog.com/2017/05/oss-fuzz-five-months-later-and.html

[9] OWASP Foundation. (2021). *OWASP Top Ten 2021*. Open Web Application Security Project. Retrieved from https://owasp.org/www-project-top-ten/

---

## Further Reading

| Resource | What It Covers |
|---|---|
| [OWASP Top 10](https://owasp.org/www-project-top-ten/) | The definitive reference for critical web vulnerability categories; free, regularly updated |
| [PortSwigger Web Security Academy](https://portswigger.net/web-security) | Free, hands-on labs for every OWASP Top 10 category; best free developer security training available |
| [OWASP SAMM](https://owaspsamm.org) | Framework for measuring and improving software security program maturity |
| Shostack, *Threat Modeling: Designing for Security* (Wiley, 2014) | The most complete book on threat modeling; written by the developer of STRIDE |
| [Microsoft SDL](https://www.microsoft.com/en-us/securityengineering/sdl) | Microsoft's Security Development Lifecycle documentation; free, battle-tested |
| [Secure Code Warrior](https://www.securecodewarrior.com) | Developer-focused security training tied to specific languages and frameworks |

---

*Questions about secure development, SSDLC implementation, or developer security training? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back -- this book is open source and your additions are welcome.*
