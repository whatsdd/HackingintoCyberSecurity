# Security Design Principles

## Why Principles Matter

Security controls fail. Patches get missed. Configurations drift. Attackers find new techniques. No specific control remains valid forever.

What does remain valid is the reasoning behind controls. Security design principles are the underlying logic that explains why certain controls work, why certain architectures are more resilient, and why certain decisions made in system design consistently lead to breaches decades later.

In 1975, Jerome Saltzer and Michael Schroeder published "The Protection of Information in Computer Systems" in the Proceedings of the IEEE. The paper introduced eight design principles for secure systems.[1] Those principles have proven more durable than any specific technology from that era. They are still cited, still taught, and still violated in systems being built today.

This chapter covers the classic principles, their modern interpretations, and the newer principles that have emerged from decades of experience building and breaking real systems.

---

## The Saltzer and Schroeder Principles

### 1. Economy of Mechanism (Keep It Simple)

> "Keep the design as simple and small as possible."

Complexity is the enemy of security. Every additional feature, every additional code path, every additional configuration option is a potential hiding place for vulnerabilities. Simple systems are easier to analyze, easier to test, easier to audit, and easier to reason about under adversarial conditions.

**In practice:**

The Heartbleed vulnerability (CVE-2014-0160) existed in a feature called "heartbeat" added to OpenSSL. The heartbeat feature sent a small message and expected a response of the same size -- but the implementation did not verify that the response was actually the size claimed. An attacker could request a 64KB response to a 1-byte heartbeat, leaking 64KB of server memory per request -- potentially including private keys, session tokens, and passwords.[2]

The feature was unnecessary for the core cryptographic function. Its complexity introduced a critical vulnerability that affected an estimated 17% of secure web servers at the time of disclosure.

{% hint style="info" %}
**Modern application:** Prefer managed services over self-hosted complexity where security is not your core competency. Fewer lines of code means fewer vulnerabilities. Remove features and dependencies that are not actively used. Every library you include is attack surface you are responsible for.
{% endhint %}

### 2. Fail-Safe Defaults (Deny by Default)

> "Base access decisions on permission rather than exclusion."

Systems should default to the secure state. If an action is not explicitly permitted, it should be denied. If a service fails, it should fail closed -- not open.

The inverse -- building systems that allow everything except what is explicitly denied -- produces security that is permanently one missed rule away from failure. Allowlists are inherently more secure than denylists because new attacks are unknown and therefore not in the denylist.

**In practice:**

A firewall configured with a default-allow policy requires administrators to enumerate every dangerous connection to block. A firewall configured with a default-deny policy requires administrators to enumerate only the connections that are legitimate. The latter produces a dramatically smaller and more auditable rule set.

The same principle applies to IAM (Identity and Access Management): new principals should receive zero permissions by default. Permissions should be explicitly granted for specific resources and actions, not inherited broadly.

```
# Bad: Overly permissive IAM policy
{
  "Effect": "Allow",
  "Action": "*",
  "Resource": "*"
}

# Good: Least-permissive policy for a specific function
{
  "Effect": "Allow",
  "Action": ["s3:GetObject"],
  "Resource": "arn:aws:s3:::my-bucket/reports/*"
}
```

### 3. Complete Mediation (Check Every Access)

> "Every access to every object must be checked for authority."

Access control decisions should not be cached, assumed, or skipped for performance. Every time a subject requests access to an object, the authorization should be verified against current permissions -- not permissions that were valid when the session started.

**In practice:**

Insecure Direct Object Reference (IDOR) -- one of the most common web application vulnerabilities -- is a failure of complete mediation. An application authenticates the user once but then uses a predictable identifier (user ID, order number) without re-verifying that the authenticated user is actually authorized to access that specific object. Change the ID in the URL, access someone else's data.

```
# Vulnerable: Authorization checked at login but not at each resource access
GET /api/invoices/12345

# The server returns invoice 12345 to any authenticated user
# It does not verify that the authenticated user owns invoice 12345
```

Every API endpoint must independently verify that the authenticated principal is authorized to perform the requested action on the requested resource.

### 4. Open Design (Security Through Obscurity Fails)

> "The design should not be secret."

A system's security should not depend on the secrecy of its design or implementation. It should remain secure even when the attacker knows exactly how it works -- because the attacker's ignorance cannot be relied upon.

This is Kerckhoffs's principle, independently derived: assume the adversary knows your algorithm. Your security comes from the secrecy of the key, not the algorithm.[3]

**In practice:**

Proprietary encryption algorithms developed by vendors who refuse to publish their design for review have a consistent track record of failure when they are eventually reverse-engineered. The A5/1 cipher used in early GSM mobile communications was kept secret, but was reverse-engineered and found to be significantly weaker than publicly designed alternatives.[4]

Open design enables peer review. The AES algorithm was published and subjected to five years of cryptanalysis by the world's best cryptographers before NIST standardized it. That review process gives users justified confidence in its security.

{% hint style="warning" %}
**Open design does not mean exposing your secrets.** It means the security mechanism does not depend on the mechanism being unknown. Your database schema being private is fine. Your encryption algorithm requiring secrecy to be secure is not.
{% endhint %}

### 5. Separation of Privilege (Two Keys to Unlock)

> "Where feasible, a protection mechanism that requires two keys to unlock it is more robust and flexible than one that allows access to the presenter of only a single key."

No single individual or component should have sufficient authority to complete a critical action alone. Requiring multiple independent conditions to be satisfied -- or multiple independent parties to authorize an action -- prevents a single point of failure or a single compromised account from causing catastrophic harm.

**In practice:**

Multi-factor authentication is a direct implementation: something you know (password) AND something you have (hardware token) AND/OR something you are (biometric). A compromised password alone is insufficient.

Code deployment pipelines that require both a developer approval and a security scan to pass before deployment can proceed implement separation of privilege. A compromised developer account cannot deploy malicious code unilaterally.

Financial controls requiring dual authorization for transfers above a threshold are the physical security analog. The Verizon DBIR consistently shows that the presence of MFA reduces the effectiveness of credential-based attacks dramatically.[5]

### 6. Least Privilege (Minimum Necessary Access)

> "Every program and every user of the system should operate using the least set of privileges necessary to complete the job."

Principals -- users, service accounts, processes -- should have exactly the permissions required for their current task and no more. This limits the blast radius of a compromise: an attacker who gains access to a low-privilege account or process inherits only those limited permissions.

**In practice:**

A web application service account that only needs to read from a specific database table should have `SELECT` permission on that table only -- not `db_owner`, not `INSERT`, not access to other tables. If the application is compromised, the attacker's database access is bounded by what the service account can do.

The principle applies at every layer:

| Layer | Least Privilege Application |
|---|---|
| Operating system | Run services as non-root; use dedicated service accounts |
| Application | Request only OAuth scopes actually needed |
| Database | Grant table-level and operation-level permissions, not schema-wide |
| Cloud IAM | Scope policies to specific resources and actions |
| Network | Allow only required ports and protocols; block everything else |

### 7. Least Common Mechanism (Minimize Shared Resources)

> "Minimize the amount of mechanism common to more than one user and depended on by all users."

Mechanisms shared between multiple users or processes are potential covert channels -- ways for one user to observe or influence another's behavior through side effects. Shared resources also mean that a compromise of the shared mechanism affects all users who depend on it.

**In practice:**

Containerization and microservices architectures implement this principle: each service runs in its own isolated environment with its own resources. A vulnerability in one service does not automatically compromise others sharing the same process space.

Multi-tenant cloud environments must carefully implement this principle. Side-channel attacks like Spectre and Meltdown (2018) exploited shared CPU cache to leak information between processes -- a direct violation of this principle at the hardware level.[6]

### 8. Psychological Acceptability (Usable Security)

> "It is essential that the human interface be designed for ease of use, so that users routinely and automatically apply the protection mechanisms correctly."

Security mechanisms that are difficult to use will be circumvented. Users will write passwords on sticky notes, disable security software that slows their machines, share accounts to avoid complicated provisioning processes, or find workarounds for controls they cannot easily comply with.

**In practice:**

Password managers solve the usability vs. security tension in password management: users no longer need to remember complex, unique passwords for every account. The security outcome (unique, complex passwords everywhere) is achieved through a tool that is easier to use than the insecure alternative (reusing simple passwords).

Phishing-resistant MFA (hardware keys like YubiKey, passkeys) is more secure than TOTP codes and, for technical users, no harder to use. The adoption of passwordless authentication is as much a usability project as a security one.

Security controls that generate too many false positives train users to ignore alerts -- which is exactly the condition that allowed the Target breach to go undetected despite automated alerts firing.[7]

---

## Modern Principles

The 1975 list was developed for timesharing systems. Subsequent decades of experience -- networked systems, the internet, cloud computing, mobile -- have produced additional principles that are now as foundational.

### Defense in Depth

No single security control is sufficient. Security architecture should layer independent controls such that the failure of any single layer does not result in a complete compromise. An attacker who bypasses the firewall should still face network segmentation. An attacker who gains a foothold on a workstation should face endpoint detection. An attacker who extracts data should find it encrypted.

Each layer independently reduces the probability of successful attack. Layers that address different threat vectors (network, endpoint, application, data) and are operated by different teams provide the strongest independence.

### Zero Trust Architecture

Zero Trust is an architectural philosophy that abandons the assumption of a trusted internal network. The traditional model -- trust everything inside the firewall, distrust everything outside -- fails catastrophically when a threat actor gains internal access (through phishing, VPN compromise, or insider action), because internal traffic is largely unmonitored and unrestricted.

Zero Trust replaces the network perimeter with identity as the new perimeter. NIST SP 800-207 defines Zero Trust as:[8]

> "Never trust, always verify. Assume breach. Verify explicitly."

| Traditional Model | Zero Trust Model |
|---|---|
| Trust based on network location (inside = trusted) | Trust based on verified identity + device health + context |
| Wide lateral movement possible once inside | Micro-segmentation limits blast radius |
| Implicit trust for internal traffic | All traffic authenticated and authorized |
| VPN provides broad network access | Just-in-time, just-enough access to specific resources |

Zero Trust is not a product -- it is an architecture. Implementing it requires investment in identity infrastructure (strong MFA everywhere), device health verification (MDM/EDR integration), micro-segmentation (software-defined networking), and continuous monitoring.

### Secure by Default

Systems should be secure out of the box, without requiring administrators to take additional hardening steps. Default configurations should be the most secure configurations. Insecure features should require explicit opt-in.

**Failures of this principle:**

- Network devices shipped with default credentials that users must actively change (Mirai botnet exploited this at scale)
- Cloud services where storage is publicly accessible by default (multiple major breaches from misconfigured S3 buckets)
- Software where debug endpoints are enabled in production builds
- Services where logging and monitoring must be manually enabled

Microsoft's "Secure by Default" initiative and Google's approach to Android security both operationalize this principle: security improvements that do not require user action reach 100% of the user base; those requiring opt-in reach a fraction.

### Minimize Attack Surface

The attack surface is the sum of all points where an attacker could attempt to enter a system. Reducing it -- by disabling unused services, removing unnecessary accounts, eliminating unneeded network exposures, and reducing code complexity -- reduces the number of opportunities for compromise.

This is distinct from defense in depth (which layers controls over existing attack surface) -- attack surface reduction eliminates the attack surface entirely.

---

## Principles in Conflict

Security design principles sometimes conflict, and resolving those conflicts requires judgment.

| Conflict | Example | Resolution Approach |
|---|---|---|
| Usability vs. Least Privilege | Complex permission management drives users to request excessive permissions | Invest in tooling that makes least-privilege easy (permission wizards, role templates) |
| Complete Mediation vs. Performance | Checking every database access adds latency | Cache decisions with short TTLs; use policy engines (OPA, Cedar) that evaluate quickly |
| Open Design vs. Business Confidentiality | Publishing security architecture exposes business logic | Separate security mechanisms (which should be open) from business logic (which may be private) |
| Defense in Depth vs. Economy of Mechanism | Adding layers increases complexity | Prefer independent layers that each address different threat vectors; avoid redundant controls |

There is no formula for these trade-offs. Security architecture is engineering judgment applied under constraints. The principles provide the vocabulary and reasoning framework; application requires understanding the specific system, threat model, and organizational context.

---

## References

[1] Saltzer, J. H., & Schroeder, M. D. (1975). The protection of information in computer systems. *Proceedings of the IEEE*, 63(9), 1278--1308. doi:10.1109/PROC.1975.9939

[2] Durumeric, Z., Kasten, J., Bailey, M., & Halderman, J. A. (2014). Analysis of the HTTPS certificate ecosystem. *Proceedings of the ACM Internet Measurement Conference*, 2014. doi:10.1145/2663716.2663755

[3] Kerckhoffs, A. (1883). La cryptographie militaire. *Journal des sciences militaires*, 9, 5--38.

[4] Barkan, E., Biham, E., & Keller, N. (2008). Instant ciphertext-only cryptanalysis of GSM encrypted communication. *Journal of Cryptology*, 21(3), 392--429. doi:10.1007/s00145-007-9001-y

[5] Verizon. (2024). *2024 Data Breach Investigations Report*. Verizon Business. Retrieved from https://www.verizon.com/business/resources/reports/dbir/

[6] Kocher, P., Horn, J., Fogh, A., Genkin, D., Gruss, D., Haas, W., Hamburg, M., Lipp, M., Mangard, S., Prescher, T., Schwarz, M., & Yarom, Y. (2019). Spectre attacks: Exploiting speculative execution. *Communications of the ACM*, 62(7), 93--101. doi:10.1145/3399742

[7] Krebs, B. (2014, February 12). Target hackers broke in via HVAC company. *Krebs on Security*. Retrieved from https://krebsonsecurity.com/2014/02/target-hackers-broke-in-via-hvac-company/

[8] Rose, S., Borchert, O., Mitchell, S., & Connelly, S. (2020). *Zero Trust Architecture*. NIST Special Publication 800-207. doi:10.6028/NIST.SP.800-207

---

## Further Reading

| Resource | What It Covers |
|---|---|
| Saltzer & Schroeder (1975) | The original paper; still worth reading in full. Available via IEEE. |
| [NIST SP 800-207](https://csrc.nist.gov/publications/detail/sp/800-207/final) | The authoritative Zero Trust Architecture guide from NIST. Free. |
| Shostack, *Threat Modeling: Designing for Security* (Wiley, 2014) | Applies design principles in the context of practical threat modeling. |
| [OWASP Security Design Principles](https://owasp.org/www-project-developer-guide/draft/design/web_app_checklist/design_principles/) | OWASP's application of design principles to web security. |
| Anderson, R. (2020). *Security Engineering* (3rd ed.). Wiley. | The most comprehensive text on security design; free online edition available. |

---

*Questions about security architecture, design principles, or applying Zero Trust? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back -- this book is open source and your additions are welcome.*
