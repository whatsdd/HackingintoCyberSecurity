# Information Security

## InfoSec and Cybersecurity Are Not the Same Thing

The terms get used interchangeably in casual conversation, but they describe different scopes of protection.

**Information security** covers all forms of information, regardless of format. A locked filing cabinet protecting paper records is an information security control. So is a clean desk policy or a procedure governing how employees handle confidential phone calls. Information security is the broader discipline: the protection of information in any form against any threat.

**Cybersecurity** is a subset of information security that specifically addresses digital systems and the threats that target them. All cybersecurity is information security, but not all information security is cybersecurity.[1]

This distinction matters in practice. An organization that focuses only on technical cybersecurity controls while ignoring physical security, personnel vetting, and process controls is leaving significant gaps. The most sophisticated intrusion detection system in the world does not help if an attacker can walk into your server room unchallenged.

---

## The CIA Triad

The CIA Triad is the foundational model of information security, defining the three properties every security program is designed to protect. The Committee on National Security Systems (CNSS) defines information security as "the protection of information and its critical components, including the systems and hardware that use, store, and transmit the information," explicitly built around these three properties.[2]

**Confidentiality** means that information is accessible only to those authorized to see it. Confidentiality controls include access management, encryption, data classification, and need-to-know policies. A breach of confidentiality occurs any time unauthorized parties access information they should not have, whether through a technical exploit, a misconfigured storage bucket, or an employee emailing the wrong attachment.

**Integrity** means that information is accurate and has not been modified without authorization. Integrity controls include cryptographic hashing, digital signatures, audit logging, and change management processes. A breach of integrity occurs when data is altered, corrupted, or deleted without proper authorization, whether by an attacker manipulating records or a failed disk write corrupting a database.

**Availability** means that systems and data are accessible when needed by authorized users. Availability controls include redundancy, backup systems, disaster recovery planning, and DDoS mitigation. A breach of availability occurs when systems go offline or data becomes inaccessible, whether through ransomware, hardware failure, or a misconfigured update pushed at 2am.

Modern practitioners sometimes extend the triad with additional properties. **Non-repudiation** ensures that parties cannot deny having performed an action, which is critical for digital transactions and legal evidence. **Authenticity** ensures that information originates from the claimed source. Donn Parker's Hexad model adds Possession, Authenticity, and Utility to the original three as a more complete framework for evaluating information security.[3]

---

## Key Concepts

These terms appear constantly in information security work. Knowing them precisely matters more than it might seem, because imprecise language leads to imprecise thinking, and imprecise thinking in security leads to gaps.

**Asset**: Anything of value that requires protection. Assets can be physical (hardware, facilities), logical (software, data, configurations), or human (staff with specialized knowledge or access). Information assets — the data and systems that process it — are the primary focus of most information security programs.

**Threat**: A potential event or actor that could cause harm to an asset. Threats include external attackers, malicious insiders, negligent employees, natural disasters, and system failures. A threat does not need to be intentional to be relevant.

**Vulnerability**: A weakness in a system, process, or control that a threat could exploit. An unpatched software flaw is a vulnerability. So is an unlocked server room, a weak password policy, or an employee who has never received security awareness training.

**Risk**: The probability that a specific threat will exploit a specific vulnerability, multiplied by the resulting impact. Risk is the product of likelihood and consequence. Information security programs are fundamentally risk management programs: the goal is not to eliminate all risk (impossible) but to reduce risk to an acceptable level given the organization's risk appetite.[4]

**Exploit**: A technique, tool, or piece of code that takes advantage of a vulnerability to cause unauthorized behavior. An exploit is the mechanism by which a threat becomes an attack.

**Control**: A safeguard or countermeasure implemented to reduce risk. Controls are categorized as technical (firewalls, encryption, access management), administrative (policies, training, incident response plans), or physical (locks, security guards, CCTV). Defense in depth means layering multiple types of controls so that the failure of any single control does not result in a breach.

**Attack surface**: The sum of all points where an attacker could attempt to enter a system or extract data. Reducing the attack surface is a primary goal of security architecture — every unnecessary service, port, user account, and application is a potential entry point.

---

## Active and Passive Attacks

Attacks on information systems fall into two broad categories based on whether they modify data or systems.

**Active attacks** involve modifying, disrupting, or destroying systems or data. Ransomware deployments, DDoS attacks, data manipulation, and unauthorized system modifications are all active attacks. Active attacks are generally easier to detect because they require the attacker to interact with systems in ways that generate observable evidence. The challenge is detecting them quickly enough to limit the damage.[5]

**Passive attacks** involve observing or collecting information without modifying anything. Network traffic sniffing, eavesdropping on unencrypted communications, and shoulder surfing are passive attacks. Passive attacks are harder to detect precisely because they leave fewer traces. The primary defense against passive attacks is ensuring that even intercepted data is unreadable, through encryption and physical access controls.

The distinction matters for defensive strategy. Preventing active attacks requires controls that block or alert on malicious actions. Preventing passive attacks often means ensuring that communications and stored data are encrypted such that interception yields nothing useful.

---

## Data Protection Laws

Information security does not operate in a legal vacuum. Organizations handling personal data are subject to a body of regulation that mandates specific controls and creates significant liability for failures.

**GDPR (General Data Protection Regulation)** is the European Union's primary data protection framework, in force since May 2018. It applies to any organization that processes personal data of EU residents, regardless of where the organization is based. Penalties for violations reach up to €20 million or 4% of global annual revenue, whichever is higher. GDPR requires organizations to implement appropriate technical and organizational measures to protect personal data, report breaches to supervisory authorities within 72 hours of becoming aware of them, and appoint a Data Protection Officer in certain circumstances.[6]

**HIPAA (Health Insurance Portability and Accountability Act)** sets US standards for protecting health information (PHI). The Security Rule mandates specific administrative, physical, and technical safeguards for electronic protected health information. Penalties range from $100 to $50,000 per violation, with an annual maximum per violation category of $1.9 million. Covered entities include healthcare providers, health plans, and healthcare clearinghouses, as well as their business associates.[7]

**CCPA (California Consumer Privacy Act)**, in force since January 2020, gives California residents rights over their personal data: the right to know what is collected, the right to delete it, and the right to opt out of its sale. It has been a model for similar legislation in other US states and signals the direction of US data protection law at the federal level.[8]

**PCI-DSS (Payment Card Industry Data Security Standard)** is a set of security requirements for organizations that handle payment card data, maintained by the Payment Card Industry Security Standards Council. Non-compliance can result in fines from card networks and loss of the ability to process card payments. Version 4.0, released in 2022, introduced more flexibility in how requirements can be met while expanding scope to address modern attack techniques.[9]

Understanding which regulations apply to an organization is foundational work for GRC roles. But even technical practitioners need awareness of these frameworks because regulatory requirements directly shape what security controls organizations must implement and document.

---

## Information Security Policies

An information security policy is the formal foundation of an organization's security program. It defines what must be protected, who is responsible, what behavior is acceptable, and what the consequences of violations are.

A policy that is not communicated, understood, and enforced is not a policy. It is a document. For a policy to be genuinely enforceable, it must meet five conditions, as established in information security governance frameworks:[10]

1. **Dissemination**: The policy must reach all relevant parties, in a form they can access and understand. Posting it on an intranet page nobody visits does not count.
2. **Comprehension**: The organization must be able to demonstrate that employees understood the requirements, not just received the document.
3. **Compliance**: Employees must formally acknowledge agreement with the policy, typically through signed acceptance or electronic attestation at system login.
4. **Uniform enforcement**: Policies must be enforced consistently across the organization. Selective enforcement creates legal liability and undermines the program's credibility.
5. **Regular review**: Policies must be updated when the threat environment, technology landscape, or regulatory requirements change. A policy last reviewed in 2019 is not a current policy.

Policies sit above procedures (the specific steps to implement them) and standards (the technical specifications). All three are necessary. An organization with policies but no procedures leaves employees unable to act on them. An organization with procedures but no policies has no formal basis for enforcing them.

---

## The Major Threats

The threats that occupy security teams are not random. They concentrate in predictable areas.

**Unpatched systems** remain the most consistently exploited class of vulnerability. Attackers routinely use publicly known exploits against systems where patches have been available for months or years. The 2017 Equifax breach, which exposed the personal data of 147 million people, was traced to an unpatched Apache Struts vulnerability for which a patch had been available for two months prior to the breach.[11]

**Social engineering** exploits human psychology rather than technical vulnerabilities. Phishing, pretexting, and business email compromise target the humans who operate systems, bypassing technical controls entirely. A technically perfect network can be compromised by a single employee who receives a convincing phone call and provides their credentials to an attacker pretending to be IT support.

**Misconfigured systems** have caused some of the largest data breaches of the past decade. Misconfigured cloud storage, overly permissive access controls, and exposed management interfaces are pervasive in organizations that have moved to cloud infrastructure at speed without corresponding investment in security expertise.[12]

**Credential compromise** through phishing, password reuse, or credential-stuffing attacks is the most common initial access technique across confirmed breaches. Multi-factor authentication (MFA) significantly reduces credential-based attacks. CISA data shows that organizations with MFA deployed broadly are substantially harder to compromise through stolen credentials than those relying on passwords alone.[13]

**Insider threats**, both malicious and accidental, account for a significant proportion of data loss events. Security programs that focus exclusively on external threats miss a substantial portion of the actual risk.

---

## References

[1] Von Solms, Rossouw; van Niekerk, Johan (2013). "From information security to cyber security". *Computers & Security*. 38: 97–102. doi:10.1016/j.cose.2013.04.004.

[2] Committee on National Security Systems (2010). *National Information Assurance (IA) Glossary*. CNSS Instruction No. 4009. US Government. Retrieved from dni.gov

[3] Parker, Donn B. (1998). *Fighting Computer Crime: A New Framework for Protecting Information*. Wiley. ISBN 978-0-471-16378-6.

[4] ISACA (2012). *COBIT 5 for Risk*. ISACA. ISBN 978-1-60420-293-4.

[5] Stallings, William; Brown, Lawrie (2018). *Computer Security: Principles and Practice* (4th ed.). Pearson. ISBN 978-0-13-477373-5.

[6] European Parliament and Council of the European Union (2016). "Regulation (EU) 2016/679 — General Data Protection Regulation". *Official Journal of the European Union*. L 119: 1–88. Retrieved from gdpr-info.eu

[7] US Department of Health and Human Services (2003). "Security Standards for the Protection of Electronic Protected Health Information". *Federal Register*. 68 (34): 8333–8381. Retrieved from hhs.gov/hipaa

[8] State of California (2018). "California Consumer Privacy Act of 2018". *California Civil Code*, Sections 1798.100–1798.199. Retrieved from oag.ca.gov/privacy/ccpa

[9] PCI Security Standards Council (2022). *Payment Card Industry Data Security Standard Requirements and Testing Procedures, Version 4.0*. PCI SSC. Retrieved from pcisecuritystandards.org

[10] Whitman, Michael E.; Mattord, Herbert J. (2021). *Principles of Information Security* (7th ed.). Cengage Learning. ISBN 978-0-357-50643-1.

[11] Federal Trade Commission (2019). "Equifax Data Breach Settlement". FTC. Retrieved 2024 from ftc.gov/enforcement/refunds/equifax-data-breach-settlement

[12] Unit 42, Palo Alto Networks (2022). *2022 Unit 42 Cloud Threat Report*. Palo Alto Networks. Retrieved 2024 from paloaltonetworks.com

[13] CISA (2022). "More Than a Password: MFA". Cybersecurity and Infrastructure Security Agency. Retrieved 2024 from cisa.gov/mfa

---

## Further Reading

**NIST Special Publication 800-53, Revision 5** (csrc.nist.gov/publications/detail/sp/800-53/rev-5/final): The comprehensive catalog of security and privacy controls used across federal and commercial organizations. Dense, but the most complete reference document in the field. [csrc.nist.gov](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)

**GDPR Full Text** (gdpr-info.eu): A clean, searchable version of the GDPR with articles and recitals clearly presented. Essential reference for anyone working in data protection or GRC. [gdpr-info.eu](https://gdpr-info.eu)

**Whitman, Michael E. and Mattord, Herbert J. — *Principles of Information Security* (7th ed., Cengage, 2021, ISBN 978-0-357-50643-1)**: The most widely used academic textbook in information security programs. Comprehensive and well-structured. If you want a single text covering the entire scope of the field, this is it.

**SANS Reading Room** (sans.org/reading-room): Free practitioner-written white papers on every aspect of information security. The quality is consistently high. [sans.org/reading-room](https://www.sans.org/reading-room/)

**Verizon DBIR** (verizon.com/business/resources/reports/dbir/): The annual Data Breach Investigations Report is the best single source for understanding what threats actually affect organizations in the real world, based on analysis of confirmed incidents rather than theoretical models.

---

*Questions about information security concepts or how they apply to your career path? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back — this book is open source and your additions are welcome.*
