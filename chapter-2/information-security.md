# Information Security

## InfoSec and Cybersecurity Are Not the Same Thing

Picture two scenarios.

In the first, an attacker exploits an unpatched vulnerability in a public-facing web server and exfiltrates a customer database. That is a cybersecurity failure.

In the second, a visitor to your office tailgates through a secured door, sits at an unlocked workstation, and photographs confidential documents left on a desk. No computer was hacked. No code was written. But information was compromised.

Both are information security failures. Only one is a cybersecurity failure.

**Information security** covers all forms of information, regardless of format. It is the broader discipline: protecting information in any form against any threat -- technical, physical, human, or environmental. A locked filing cabinet is an information security control. So is a visitor sign-in policy, a clean desk requirement, and a procedure for securely disposing of printed materials.

**Cybersecurity** is a subset of information security that specifically addresses digital systems and the threats that target them.[1] All cybersecurity is information security, but the reverse is not true.

This distinction has practical consequences. An organization that invests heavily in technical security controls while leaving its physical premises accessible, its staff untrained, and its paper records unprotected has not secured its information. It has secured one layer of a multi-layer problem.

---

## The CIA Triad

Every information security program is built around three properties. Protecting them is the work. Failing to protect any one of them constitutes a security incident. The Committee on National Security Systems (CNSS) grounds its definition of information security explicitly in all three.[2]

| Property | Definition | Common Controls | Example of a Breach |
|---|---|---|---|
| **Confidentiality** | Information is accessible only to authorized parties | Access management, encryption, data classification, need-to-know policies | A misconfigured S3 bucket exposes 100 million customer records publicly |
| **Integrity** | Information is accurate and unmodified without authorization | Cryptographic hashing, digital signatures, audit logs, change management | An attacker modifies financial records; a failed update corrupts a database |
| **Availability** | Systems and data are accessible when authorized users need them | Redundancy, backups, DDoS mitigation, disaster recovery planning | Ransomware encrypts a hospital's systems; a misconfigured update takes production offline |

No property takes precedence. An organization that achieves perfect confidentiality and integrity but whose systems are unavailable when needed has failed. A system that is always available but leaks data or allows modification without authorization has equally failed.

### Beyond the Triad

Modern practitioners extend the CIA model with additional properties. **Non-repudiation** ensures that parties cannot deny having performed an action -- critical for digital transactions, contracts, and legal evidence. Digital signatures achieve non-repudiation. **Authenticity** ensures that information originates from the claimed source.

Donn Parker's Hexad model formalizes these extensions, adding Possession, Authenticity, and Utility to the original three.[3] The Hexad is worth knowing because it appears in advanced certifications and frameworks, and it covers failure modes the triad misses.

---

## Key Concepts

These terms appear constantly in information security work. Imprecise language leads to imprecise thinking, and imprecise thinking in security leads to gaps in coverage.

{% hint style="info" %}
**Asset:** Anything of value that requires protection. Assets include physical resources (hardware, facilities), logical resources (data, software, configurations), and human resources (staff with specialized knowledge or privileged access). Asset inventories are the foundation of risk management -- you cannot protect what you have not identified.

**Threat:** A potential event or actor that could cause harm to an asset. Threats can be external (attackers), internal (malicious or negligent insiders), environmental (fire, flood, power failure), or accidental (human error). A threat does not need to be intentional to be relevant.

**Vulnerability:** A weakness that a threat could exploit. An unpatched software flaw is a vulnerability. So is an unlocked server room, a default credential left unchanged, a weak password policy, or an employee who has never received security awareness training.

**Risk:** The product of likelihood and impact. Risk = Probability that a specific threat exploits a specific vulnerability × Consequence of that event. Information security programs are risk management programs -- the goal is not to eliminate all risk (that is impossible) but to reduce risk to an acceptable level given the organization's risk appetite.[4]

**Exploit:** A technique, tool, or piece of code that takes advantage of a vulnerability to cause unauthorized behavior. An exploit is the mechanism by which a threat becomes an actual attack.

**Control:** A safeguard implemented to reduce risk. Controls are categorized as technical (firewalls, encryption, endpoint detection), administrative (policies, training, incident response plans), or physical (locks, cameras, access badges). Defense in depth means layering multiple control types so that the failure of any single control does not result in a breach.

**Attack surface:** The total set of points where an attacker could attempt to enter a system or extract data. Every unnecessary open port, user account, application, and network service is a potential entry point. Reducing the attack surface is a primary goal of security architecture.
{% endhint %}

---

## Active and Passive Attacks

Attacks on information systems differ fundamentally in how they interact with data, which shapes both how they are detected and how they are prevented.[5]

### Active Attacks

Active attacks modify, disrupt, or destroy systems or data. The attacker does something that changes the state of a system.

| Active Attack Type | What Happens | Detection Difficulty |
|---|---|---|
| Ransomware deployment | Files are encrypted; systems become unavailable | Moderate -- generates file system and network activity |
| Data manipulation | Records are altered to deceive or corrupt | Hard -- requires integrity monitoring to detect |
| DDoS | Systems are flooded until unavailable | Easy -- visible in network traffic immediately |
| Unauthorized modification | System configurations or code is changed | Moderate -- requires change monitoring |

Active attacks are generally detectable because they generate observable evidence: log entries, file system changes, network anomalies. The challenge is detecting them quickly enough to limit damage -- not after the damage is done.

### Passive Attacks

Passive attacks collect or observe information without modifying anything.

| Passive Attack Type | What Happens | Detection Difficulty |
|---|---|---|
| Network traffic sniffing | Unencrypted traffic is captured and read | Very hard -- attacker generates no network noise |
| Eavesdropping | Verbal or electronic communications are monitored | Very hard -- no system interaction |
| Shoulder surfing | Screens or keyboards are visually observed | Extremely hard -- no digital trace |
| OSINT collection | Public information about targets is gathered | Impossible to detect |

Passive attacks leave few or no traces. The primary defense is ensuring that even successfully intercepted data is unreadable -- through encryption, physical access controls, and limiting what information is publicly available about your organization and its people.

---

## Data Protection Laws

Information security does not operate in a legal vacuum. Organizations handling personal data are subject to regulation that mandates specific controls and creates significant liability for failures. Understanding the applicable regulatory landscape is foundational work for GRC roles and increasingly relevant for every technical practitioner.

| Regulation | Scope | Key Requirement | Maximum Penalty |
|---|---|---|---|
| **GDPR** | Any org processing EU residents' data, globally | Report breaches within 72 hours; implement appropriate technical and organizational measures; appoint DPO in specified cases | €20M or 4% of global annual revenue, whichever is higher [6] |
| **HIPAA** | US healthcare providers, plans, clearinghouses, and their business associates | Specific administrative, physical, and technical safeguards for electronic protected health information | $100 to $50,000 per violation; $1.9M annual maximum per category [7] |
| **CCPA** | Organizations processing California residents' data above defined thresholds | Right to know, right to delete, right to opt out of data sale | $2,500 per unintentional violation; $7,500 per intentional violation [8] |
| **PCI-DSS** | Any organization handling payment card data | 12 high-level requirements across network security, access control, monitoring, and policy | Fines from card networks; potential loss of ability to process card payments [9] |

{% hint style="warning" %}
**Which regulation applies to you?** Many organizations are subject to multiple frameworks simultaneously. A US healthcare company operating in Europe with a payment processing function is subject to HIPAA, GDPR, and PCI-DSS at the same time. These frameworks sometimes have conflicting requirements. Compliance is not a checkbox exercise -- it is ongoing legal and technical work.

When in doubt, involve legal counsel. Regulatory penalties are only the floor of the liability. Class action lawsuits, regulatory investigations, and reputational damage can dwarf the direct fines.
{% endhint %}

---

## Information Security Policies

An information security policy is the formal foundation of an organization's security program. It defines what must be protected, who is responsible for protecting it, what behaviors are acceptable, and what the consequences of violations are.

A policy that is not communicated, understood, and enforced is not a policy. It is a document, possibly a liability, and definitely not a control.

For a policy to be genuinely enforceable -- including as a basis for disciplinary action or legal proceedings -- it must meet five conditions established in information security governance literature.[10]

{% hint style="info" %}
**The Five Enforceability Conditions:**

1. **Dissemination** -- The policy must reach all relevant parties in a form they can access and understand. Posting it on an intranet page that 3% of employees have visited does not meet this bar.

2. **Comprehension** -- The organization must be able to demonstrate that employees understood the requirements, not merely received the document. This typically requires testing, training completion records, or manager attestation.

3. **Compliance acknowledgment** -- Employees must formally acknowledge agreement, typically through signed acceptance or electronic attestation at system login. This creates the legal basis for enforcement.

4. **Uniform enforcement** -- Policies must be enforced consistently. Selective enforcement (applying rules to junior staff but not executives) creates legal liability and destroys the program's credibility with employees.

5. **Regular review** -- Policies must be updated when the threat environment, technology landscape, or regulatory requirements change. A policy last reviewed three years ago is functionally outdated and may no longer reflect legal requirements.
{% endhint %}

Policies sit above procedures (the specific steps to implement them) and standards (the technical specifications that define how systems must be configured). All three are necessary. Organizations with policies but no procedures leave employees unable to act on them. Organizations with procedures but no policies have no formal basis for requiring or enforcing them.

---

## The Major Threats

The threats that occupy security teams are not random. They cluster in predictable areas, and the same failure modes appear across industries, geographies, and organization sizes year after year.

### Unpatched Systems

The most consistently exploited vulnerability class is not sophisticated zero-days. It is publicly known vulnerabilities against which patches have been available for months or years.

{% hint style="danger" %}
**The Equifax breach (2017):** Attackers exploited CVE-2017-5638, a critical vulnerability in Apache Struts -- an open-source web framework. A patch had been available for two months before the breach began. Equifax had failed to apply it. The breach exposed the personal data of 147 million Americans, including Social Security numbers, birth dates, addresses, and driver's license numbers. The FTC settlement totalled $575 million.[11]

The vulnerability was public. The patch was available. The attacker used a widely available exploit. None of the technical sophistication was on the attacker's side.
{% endhint %}

Patch management -- the unglamorous, operationally complex process of tracking software vulnerabilities and deploying updates across a large environment -- prevents more breaches than any other single control.

### Misconfigured Systems

Misconfiguration has caused some of the largest data exposures of the past decade. The growth of cloud infrastructure, where organizations can provision complex systems in minutes without the friction of traditional change management, has made misconfiguration pervasive.

Misconfigured cloud storage buckets (publicly readable S3 buckets, Azure Blob containers, or Google Cloud Storage) have exposed health records, financial data, insurance claims, and government documents at scale. The 2019 Capital One breach, which exposed data from 100 million customers, originated from a misconfigured web application firewall running on AWS.[12]

### Credential Compromise

Compromised credentials are the most common initial access vector across confirmed breaches. Once an attacker has valid credentials, they can authenticate as a legitimate user -- bypassing technical controls that are designed to stop unauthorized access, not authenticated access.

Multi-factor authentication (MFA) significantly reduces credential-based attacks. An attacker with a valid password still cannot access an account if they cannot also satisfy the second factor. CISA data shows that organizations with broadly deployed MFA are substantially harder to compromise through credential attacks than those relying on passwords alone.[13]

{% hint style="success" %}
**The single highest-value control for most organizations:** Enable MFA everywhere. On email. On VPNs. On cloud consoles. On administrative accounts especially. The Cybersecurity and Infrastructure Security Agency (CISA), the FBI, and the NSA have all published joint guidance making MFA their top recommendation. It is not technically glamorous. It works.
{% endhint %}

### Social Engineering

Social engineering exploits human psychology rather than technical vulnerabilities. A technically perfect network can be compromised by a single employee who receives a convincing phone call and provides their credentials to an attacker pretending to be IT support.

The 2020 Twitter hack -- in which attackers gained access to accounts belonging to Barack Obama, Elon Musk, Joe Biden, Apple, and others to run a Bitcoin scam -- was executed not through technical hacking but through social engineering of Twitter employees to gain access to internal administrative tools. No exploit was needed. The attacker called people and persuaded them.

### Insider Threats

Insider threats -- both malicious and accidental -- account for a significant proportion of data loss events that security programs focused exclusively on external threats will miss. The challenge is that legitimate authorized access is difficult to distinguish from abuse of that access without behavioral monitoring and appropriate least-privilege controls.

---

## References

[1] Von Solms, R., & van Niekerk, J. (2013). From information security to cyber security. *Computers & Security*, 38, 97--102. doi:10.1016/j.cose.2013.04.004

[2] Committee on National Security Systems. (2022). *National Information Assurance (IA) Glossary*. CNSS Instruction No. 4009. US Government. Retrieved from https://www.cnss.gov/CNSS/issuances/Instructions.cfm

[3] Parker, D. B. (1998). *Fighting Computer Crime: A New Framework for Protecting Information*. Wiley. ISBN 978-0-471-16378-6.

[4] ISACA. (2012). *COBIT 5 for Risk*. ISACA. ISBN 978-1-60420-293-4.

[5] Stallings, W., & Brown, L. (2018). *Computer Security: Principles and Practice* (4th ed.). Pearson. ISBN 978-0-13-477373-5.

[6] European Parliament and Council of the European Union. (2016). Regulation (EU) 2016/679 -- General Data Protection Regulation. *Official Journal of the European Union*, L 119, 1--88. Retrieved from https://gdpr-info.eu

[7] US Department of Health and Human Services. (2003). Security Standards for the Protection of Electronic Protected Health Information. *Federal Register*, 68(34), 8333--8381. Retrieved from https://www.hhs.gov/hipaa/for-professionals/security/index.html

[8] State of California. (2018). *California Consumer Privacy Act of 2018*. California Civil Code, Sections 1798.100--1798.199. Retrieved from https://oag.ca.gov/privacy/ccpa

[9] PCI Security Standards Council. (2022). *Payment Card Industry Data Security Standard Requirements and Testing Procedures, Version 4.0*. PCI SSC. Retrieved from https://www.pcisecuritystandards.org

[10] Whitman, M. E., & Mattord, H. J. (2021). *Principles of Information Security* (7th ed.). Cengage Learning. ISBN 978-0-357-50643-1.

[11] Federal Trade Commission. (2019). *Equifax Data Breach Settlement*. FTC. Retrieved from https://www.ftc.gov/enforcement/refunds/equifax-data-breach-settlement

[12] US Senate Permanent Subcommittee on Investigations. (2020). *Threats to US Networks: Oversight of Chinese Government-Owned Carriers*. Retrieved from https://www.hsgac.senate.gov

[13] CISA. (2022). *More Than a Password: Implement Multi-Factor Authentication*. Cybersecurity and Infrastructure Security Agency. Retrieved from https://www.cisa.gov/sites/default/files/publications/MFA-Fact-Sheet-Jan22-508.pdf

---

## Further Reading

| Resource | What It Covers |
|---|---|
| [NIST SP 800-53 Rev 5](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final) | Comprehensive catalog of security and privacy controls. Dense but the most complete reference in the field. |
| [GDPR Full Text](https://gdpr-info.eu) | Clean, searchable version of the GDPR with articles and recitals. Essential reference for data protection work. |
| [SANS Reading Room](https://www.sans.org/reading-room/) | Free practitioner-written white papers across every aspect of information security. Consistently high quality. |
| [Verizon DBIR](https://www.verizon.com/business/resources/reports/dbir/) | Best single source for understanding what threats actually affect organizations; based on confirmed incidents. |
| Whitman & Mattord, *Principles of Information Security* (7th ed., Cengage, 2021) | Most widely used academic textbook in InfoSec programs. If you want one comprehensive text, this is it. |

---

*Questions about information security concepts or how they apply to your career path? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back -- this book is open source and your additions are welcome.*
