# Secure Developer: Building Security In

## The Most Expensive Way to Find a Bug

In 2017, Equifax's engineering team was using Apache Struts. Apache Struts had a critical remote code execution vulnerability: CVE-2017-5638. A patch was released in March. Equifax's systems were exploited in May. 147 million people's data was exposed.

The patch existed. The process to apply it did not work. But trace that further back: the vulnerability itself existed because software was shipped without adequate security review of how user input was handled. A fundamental secure coding principle, validate and sanitize all untrusted input, was not applied in a component that hundreds of thousands of applications would eventually depend on.

Security vulnerabilities are primarily software defects. And like all software defects, they are dramatically cheaper to fix when found early. NIST research on software defect costs shows that a bug found during the requirements phase costs roughly one unit to fix. The same bug found in production costs 30 times more. Found after a breach, the costs in legal fees, regulatory fines, remediation, and reputational damage multiply that by another order of magnitude.[1]

The Secure Software Development Lifecycle (SSDLC) is the discipline of building security into every phase of software development (requirements, design, implementation, testing, and deployment) rather than attempting to add it after the fact.

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

The investment in developer security training pays back measurably. Google's Project Zero data shows that most high-severity vulnerabilities exploited in the wild fall into a small number of recurring categories, categories that developers who have received targeted training reliably avoid.[2]

---

## SSDLC Models

Several frameworks formalize the integration of security into the development lifecycle.

### Microsoft Security Development Lifecycle (SDL)

The Microsoft SDL was developed in response to the Windows XP security crisis of the early 2000s, a period when Microsoft products were so widely exploited that the company's reputation was seriously threatened. Bill Gates' 2002 "Trustworthy Computing" memo redirected the entire company toward security, and SDL was the operational result.[3]

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

BSIMM differs from SDL and SAMM in that it is descriptive rather than prescriptive. It is based on observational data from security programs at real organizations, measuring what they actually do rather than what frameworks say they should do.[5] BSIMM data is useful for benchmarking: understanding how your security program compares to peers in your industry.

---

## Phase 1: Security Requirements

Security requirements are the security properties a system must have. They are defined before design begins, not discovered during testing.

**Types of security requirements:**

- **Functional security requirements**: Specific behaviors the system must implement (MFA for administrator access, AES-256 encryption for stored credentials, session timeout after 15 minutes of inactivity)
- **Non-functional security requirements**: Properties the system must exhibit (audit logging of all authentication events, response to security scan findings within defined SLAs)
- **Compliance requirements**: Security behaviors mandated by regulation (GDPR data minimization, HIPAA audit controls, PCI-DSS encryption of cardholder data)
- **Abuse cases**: Descriptions of how an attacker might try to misuse the system, the security complement to use cases

{% hint style="info" %}
**Abuse cases are underused.** A use case describes what a legitimate user does. An abuse case describes what a malicious user attempts. For a login function, the use case is "user enters valid credentials and is authenticated." Abuse cases include "attacker attempts to brute-force credentials," "attacker attempts SQL injection in the username field," "attacker replays an expired session token."

Writing abuse cases forces developers to think about the attacker's perspective before design is finalized, which is exactly when it is cheapest to prevent the corresponding vulnerability.
{% endhint %}

---

## Phase 2: Threat Modeling

Threat modeling is the systematic process of identifying what can go wrong in a system, why it can go wrong, and what to do about it. It is performed during the design phase, before implementation, when changing designs is cheap.

This book covers threat modeling in depth in **Chapter 8** — STRIDE, the data flow diagram, the four questions, and a full worked example. Rather than repeat it, this section focuses on what threat modeling looks like *inside a developer's workflow*, where it's smaller and more frequent than the big up-front system model.

**Threat model the feature, not the whole system.** As a developer, you rarely design a system from scratch; you add a feature to an existing one. The high-leverage habit is a five-minute threat model of *your change* during design or PR:

- Does this change introduce a new **trust boundary**? (a new external API call, a new file upload, a new user-supplied parameter that reaches a query)
- Does it touch **authentication or authorization**? If so, is the check on the server, and does it deny by default?
- Does it handle **untrusted input**? Where does that input end up — a database query, a shell command, an HTML page, a log?
- What's the **worst thing** an attacker who controls this input could do?

Run those four questions against the STRIDE categories (Chapter 8) and most feature-level vulnerabilities surface before the code is written. The question "what could go wrong if an attacker controls this input?" asked during design prevents far more vulnerabilities than the same question asked during a post-release penetration test.

---

## Phase 3: Secure Coding Principles

These principles apply across languages, frameworks, and domains. They are not a complete substitute for knowing the specific vulnerability classes relevant to your stack, but they are the foundation.

### Validate All Input

Every piece of data entering your system from outside your control is untrusted. This includes user input, API responses, file contents, database query results, environment variables, and headers.

- Validate input against a strict allowlist of acceptable values (not a denylist of bad values, since attackers will find what you missed)
- Reject or sanitize input that does not conform
- Never trust data from the client side, even if your client-side code validates it first

### Encode All Output

When data is output to another context (a web page, a database query, a command line, a log file), it must be encoded for that context to prevent injection. A string safe for display in HTML is not necessarily safe for inclusion in a JavaScript expression or a SQL query.

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

Least privilege limits blast radius: if a component is compromised, the attacker inherits only the permissions that component had, not the permissions of everything else on the system.

### Fail Securely

When a system encounters an error, it should fail into a secure state. Failed authentication should result in access denied, not access granted. An exception in a security check should not default to allowing the operation.

Error messages shown to users should be generic ("An error occurred"). Detailed error information should be logged internally but never returned to the client, where it provides attackers with information about the system's internals.

### Defense in Depth

Do not rely on a single security control. Layer controls so that the failure of any one does not result in a compromise. Input validation + parameterized queries is more robust than either alone. MFA + session management + audit logging is more robust than any single authentication control.

### Secure Defaults

Systems should be secure out of the box without requiring administrators to take additional action. Insecure features should require explicit opt-in, not opt-out. Default passwords should not exist. Debug endpoints should be disabled by default in production builds.

### Vulnerable vs. Fixed: Three Patterns You'll Actually Write

Principles stick when you see the code. Here are three of the most common web vulnerabilities, each as a before/after pair.

**Injection (A05) — the broken-then-fixed query you already saw above**, but the same shape applies to OS commands:

```python
# VULNERABLE: shell command built from user input
import os
os.system("ping -c 1 " + user_host)   # user_host = "x; rm -rf /"

# FIXED: pass arguments as a list; no shell interpretation
import subprocess
subprocess.run(["ping", "-c", "1", user_host], check=True)
```

**Broken Access Control (A01) — the #1 risk, and almost always missing server-side authorization:**

```python
# VULNERABLE: authenticated, but never checks ownership (IDOR)
@app.get("/api/invoices/{invoice_id}")
def get_invoice(invoice_id, user=Depends(current_user)):
    return db.get_invoice(invoice_id)        # any logged-in user reads any invoice

# FIXED: verify the resource belongs to the caller
@app.get("/api/invoices/{invoice_id}")
def get_invoice(invoice_id, user=Depends(current_user)):
    invoice = db.get_invoice(invoice_id)
    if invoice.owner_id != user.id:
        raise HTTPException(status_code=404)  # 404, not 403 — don't confirm it exists
    return invoice
```

**Cross-Site Scripting (a form of Injection) — unescaped output:**

```javascript
// VULNERABLE: untrusted data written straight into the DOM
element.innerHTML = userComment;          // <img src=x onerror=alert(1)>

// FIXED: use textContent (no HTML parsing), or a vetted sanitizer for rich text
element.textContent = userComment;
// for rich HTML: element.innerHTML = DOMPurify.sanitize(userComment);
```

### Don't Hand-Roll Validation — Use Your Framework's Tools

"Validate all input" is good advice that's easy to do badly. Every major ecosystem has vetted libraries; use them instead of ad-hoc regex:

| Language / Stack | Use For Validation / Safety |
|---|---|
| **Python** | `pydantic` for schema validation; ORM parameterization (SQLAlchemy, Django ORM); `bleach`/`nh3` for HTML sanitization |
| **JavaScript / TypeScript** | `zod` or `joi` for schema validation; `DOMPurify` for HTML; parameterized queries via the DB driver or an ORM (Prisma) |
| **Java** | Bean Validation (Jakarta `@Valid`); prepared statements / JPA; OWASP Java Encoder for output |
| **Go** | `validator` struct tags; `database/sql` parameterized queries; `html/template` (auto-escapes by default) |
| **Ruby / Rails** | Strong Parameters; ActiveRecord parameterization; Rails' default view auto-escaping |

The pattern across all of them: lean on the framework's parameterization and auto-escaping, validate with a schema library, and reserve custom validation for genuine business rules.

---

## Phase 4: Dependency Management

Modern applications are 80 to 95% open-source code. Every dependency you include carries its own vulnerability history and future CVEs. Managing that risk is an ongoing development responsibility.

{% hint style="warning" %}
**Transitive dependencies are your responsibility too.** When you include a library, you implicitly include everything that library depends on. The Log4Shell vulnerability (CVE-2021-44228) was introduced into millions of applications not through direct use of Log4j, but through third-party libraries that used it internally. Organizations discovered they were vulnerable to a critical RCE flaw in code they had never knowingly chosen to include.[7]

Run SCA (Software Composition Analysis) tools (Snyk, Dependabot, OWASP Dependency-Check) as part of your build process. Know what you are shipping.
{% endhint %}

**The threat is no longer just *vulnerable* dependencies — it's *malicious* ones.** The 2024 XZ Utils backdoor (CVE-2024-3094) changed how seriously teams take this. An attacker spent **years** building trust as a volunteer maintainer of a widely-used compression library, then slipped in an obfuscated backdoor that nearly reached production Linux distributions worldwide. A CVE scanner would not have caught it, because the vulnerability was deliberately planted, not accidentally introduced. This raises the bar for vetting:

- **Assess the maintainer and project health, not just the code.** Is it actively maintained by more than one person? Is maintenance suddenly being handed to an unknown contributor? Sudden maintainer changes on a critical low-level library are now a recognized red flag.
- **Watch for unusual update behavior.** A dependency that suddenly adds obfuscated code, build-time scripts, or new network calls deserves scrutiny.
- **Use tools built for this.** Standard SCA finds known CVEs; tools like Socket and OpenSSF Scorecard assess *supply-chain* risk signals (suspicious install scripts, maintainer changes, project health) that CVE databases miss.

Dependency management best practices:

- Pin dependency versions exactly (not ranges) to ensure reproducible builds and control when you take updates
- Automate vulnerability scanning in the CI/CD pipeline
- Review dependencies before adding them: Does this library have a security track record? Is it actively maintained by a healthy community? What is its download source? (Supply chain attacks via typosquatting are real)
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

## Authentication and Authorization: Use the Standards

Two of the OWASP Top 10 categories (Broken Access Control, Authentication Failures) come down to getting identity right — and the single best move is to *not build it yourself*. Rolling your own authentication is the secure-coding equivalent of rolling your own crypto.

- **Authentication** answers "who are you?" Delegate it where you can: OpenID Connect (OIDC), built on top of OAuth 2.0, lets you authenticate users via an identity provider (Google, Okta, Entra ID, Auth0) so you never store passwords at all. If you must handle passwords, store them with Argon2id (Chapter 7) and offer MFA.
- **Authorization** answers "what are you allowed to do?" This is *yours* to enforce — no identity provider can do it for you — and it must happen **server-side on every request** (complete mediation, Chapter 9). Use a clear model: role-based access control (RBAC) for most apps, attribute-based (ABAC) or a policy engine (OPA, Cedar) when rules get complex.
- **OAuth 2.0 is for authorization (delegated access), not authentication.** A common, dangerous mistake is using a raw OAuth access token as proof of identity. Use OIDC's `id_token` for "who is this user," and access tokens only for "what may this client call." Getting this distinction right prevents a whole class of account-takeover bugs.

The takeaway: treat authentication as a solved problem you integrate, and spend your effort on authorization, which only you can get right for your domain.

---

## Secure Coding in the Age of AI Assistants

By 2026, most developers write code with an AI assistant. That's fine — but it shifts where the security risk lives, and a secure developer adjusts.

- **AI-generated code is not secure by default.** Multiple studies have found that code from AI assistants contains vulnerabilities at rates comparable to (sometimes worse than) human-written code — and developers using assistants sometimes write *less* secure code while feeling *more* confident. The model reproduces the patterns in its training data, insecure ones included.
- **Review AI output more carefully, not less.** Treat a code suggestion like a pull request from a fast but junior contributor who doesn't know your threat model. The vulnerable-vs-fixed patterns earlier in this chapter are exactly what to check for: is input parameterized, is access checked server-side, is output escaped?
- **Run it through the same gates.** AI-written code goes through the same SAST, SCA, and code review as everything else. If anything, lean harder on automated scanning, since AI lets you produce code faster than you can manually review it.
- **Never paste secrets or sensitive code into untrusted tools.** Know your organization's policy on what can go into which assistant.

The skill that's now scarce and valuable: enough security fundamentals to catch what the AI gets wrong. That's what this chapter builds.

---

## OWASP Top 10 for Developers

The OWASP Top 10 is the most widely referenced categorization of critical web application security risks.[9] Every developer building web applications needs to understand these categories well enough to recognize and prevent them in their own code. The list below reflects the **2025 edition** (finalized in early 2026); note the changes from the long-standing 2021 list — Security Misconfiguration rose to #2, Software Supply Chain Failures entered as its own category at #3 (broadening the old "Vulnerable Components"), and Mishandling of Exceptional Conditions is new at #10.

| Rank | Category | Prevent It By |
|---|---|---|
| A01 | Broken Access Control (now includes SSRF) | Enforce authorization checks server-side; deny by default; validate/allowlist outbound URLs |
| A02 | Security Misconfiguration | Secure defaults; IaC scanning; remove unnecessary features and default accounts |
| A03 | Software Supply Chain Failures | SCA scanning; SBOMs; dependency pinning; verify provenance of components and build tooling |
| A04 | Cryptographic Failures | Use TLS everywhere; encrypt sensitive data at rest; use modern algorithms (see Chapter 7) |
| A05 | Injection | Parameterized queries; input validation; output encoding |
| A06 | Insecure Design | Threat modeling; abuse cases; security requirements before implementation |
| A07 | Authentication Failures | MFA; secure password storage (bcrypt/Argon2); account lockout |
| A08 | Software and Data Integrity Failures | Code signing; verify integrity of updates; CI/CD pipeline security |
| A09 | Security Logging and Alerting Failures | Log authentication events, access failures, privilege changes; alert on them |
| A10 | Mishandling of Exceptional Conditions | Fail securely; don't leak internals in errors; handle edge cases and "fail open" risks |

---

## Try This

1. **Find and fix the vulnerability.** Take the vulnerable code samples in this chapter (or write your own three-line login query) and, in your language of choice, write both the broken and the fixed version. Then prove the fix: try the injection/IDOR payload against both. Nothing teaches secure coding like watching your own exploit stop working.
2. **Do the OWASP labs.** Work through the [PortSwigger Web Security Academy](https://portswigger.net/web-security) labs for Broken Access Control and SQL Injection — free, hands-on, and the single best developer security training available. Each lab is a vulnerability you'll then recognize instantly in real code.
3. **Audit an AI suggestion.** Ask an AI assistant to "write a login endpoint in [your framework]." Then review its output against this chapter: does it parameterize queries, hash passwords properly, check authorization, and avoid leaking errors? Document what it got wrong. This is the exact skill employers now test for.

---

## Key Takeaways

- Security vulnerabilities are software defects, and like all defects they're far cheaper to prevent early. Security has to live with the developers, not in a gate at the end.
- Threat model your *change*, not just the whole system: new trust boundary? touches auth? handles untrusted input? worst case? (Full method in Chapter 8.)
- The recurring fixes are concrete and learnable: parameterize queries, escape output, check authorization server-side on every request, fail securely. Use your framework's vetted libraries instead of hand-rolling.
- Dependencies are most of your code and now a top risk — not just vulnerable components (Log4Shell) but maliciously planted ones (XZ Utils). Vet maintainer health, not just CVEs.
- Don't build authentication; integrate OIDC and spend your effort on authorization. Don't confuse OAuth (authorization) with authentication.
- AI writes insecure code confidently. Review its output harder, run it through the same gates, and value the fundamentals that let you catch its mistakes.
- Know the OWASP Top 10 2025 — it's both a checklist and a shared vocabulary every security interview assumes.

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

[9] OWASP Foundation. (2025). *OWASP Top Ten 2025*. Open Web Application Security Project. Retrieved from https://owasp.org/Top10/

---

## Further Reading

| Resource | What It Covers |
|---|---|
| [OWASP Top 10 (2025)](https://owasp.org/Top10/) | The definitive reference for critical web vulnerability categories; free, regularly updated |
| [PortSwigger Web Security Academy](https://portswigger.net/web-security) | Free, hands-on labs for every OWASP Top 10 category; best free developer security training available |
| [OWASP SAMM](https://owaspsamm.org) | Framework for measuring and improving software security program maturity |
| Shostack, *Threat Modeling: Designing for Security* (Wiley, 2014) | The most complete book on threat modeling; written by the developer of STRIDE |
| [Microsoft SDL](https://www.microsoft.com/en-us/securityengineering/sdl) | Microsoft's Security Development Lifecycle documentation; free, battle-tested |
| [Secure Code Warrior](https://www.securecodewarrior.com) | Developer-focused security training tied to specific languages and frameworks |

---

*Questions about secure development, SSDLC implementation, or developer security training? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back. This book is open source and your additions are welcome.*
