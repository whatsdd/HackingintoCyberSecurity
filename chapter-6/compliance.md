# Compliance

## Compliance Is Not Security. Both Matter.

In 2019, British Airways was fined £20 million by the UK Information Commissioner's Office. Attackers had compromised the airline's website and redirected customers to a fraudulent site that harvested payment card details. Around 500,000 customers were affected. The breach ran for two months before detection.

British Airways was PCI-DSS compliant at the time.

The fine was issued under GDPR. The breach violated the regulation's requirement to implement appropriate technical and organizational measures to protect personal data. Compliance with one framework did not prevent violation of another. And compliance with all applicable frameworks did not prevent the breach.[1]

This is the central tension in compliance: organizations often treat it as a destination rather than a baseline. Pass the audit. Tick the box. Move on. But compliance frameworks define the floor of acceptable security practice, not the ceiling. An organization can be fully compliant and still be breached. Security is what compliance is supposed to reflect -- but the reflection is imperfect.

Understanding compliance means understanding what it actually requires, what it does not require, and how to navigate a landscape where the requirements multiply every year.

---

## What Compliance Actually Is

Compliance is the state of adhering to laws, regulations, contractual obligations, or standards that apply to an organization. In information security, those requirements typically mandate:

- Specific technical controls (encryption, access management, logging)
- Administrative processes (policies, training, risk assessments, incident response plans)
- Physical safeguards (access controls on data centers, equipment disposal)
- Audit and accountability mechanisms (documentation, evidence collection, third-party audits)

Compliance is not optional when it is legally required. GDPR fines reach 4% of global annual revenue. HIPAA violations carry criminal penalties. PCI-DSS non-compliance can result in losing the ability to process credit cards. These are business-critical consequences.

{% hint style="info" %}
**The compliance vs. security distinction matters:**

**Compliance** asks: "Does this control exist and is it documented?"

**Security** asks: "Does this control actually reduce risk?"

A firewall that exists but is misconfigured satisfies a compliance checkbox. It does not provide security. The goal is to implement controls that are both compliant and effective -- but the two are not automatic synonyms. Organizations that treat compliance as a proxy for security, rather than as a starting point, make themselves vulnerable.
{% endhint %}

---

## The Major Compliance Frameworks

### GDPR (General Data Protection Regulation)

**Who it applies to:** Any organization, anywhere in the world, that processes personal data of individuals in the European Union or European Economic Area.

GDPR is the most expansive data protection regulation in force. It applies to a startup in Singapore if that startup collects email addresses from EU residents. It applies to a US SaaS company if EU businesses use its product to process customer data.[2]

**Key requirements:**

- **Lawful basis**: Processing personal data requires a documented lawful basis (consent, contract, legal obligation, legitimate interests, etc.)
- **Data minimization**: Collect only what is necessary for the stated purpose
- **Breach notification**: Report breaches to the supervisory authority within 72 hours of becoming aware; notify affected individuals without undue delay when high risk
- **Data subject rights**: Respond to requests for access, deletion, correction, and portability
- **Data Protection Officer (DPO)**: Required for public authorities, organizations processing data at scale, or those processing sensitive categories of data
- **Appropriate technical and organizational measures**: No specific controls mandated; must be proportionate to the risk

**Penalties:** Up to €20 million or 4% of global annual revenue, whichever is higher. In 2023, Meta was fined €1.2 billion for transferring EU user data to the US without adequate safeguards.[3]

### HIPAA (Health Insurance Portability and Accountability Act)

**Who it applies to:** US healthcare providers, health plans, healthcare clearinghouses (covered entities), and their business associates (vendors who process protected health information on their behalf).

HIPAA mandates specific controls for electronic protected health information (ePHI) through three rules:[4]

| Rule | What It Covers |
|---|---|
| **Privacy Rule** | Permitted uses and disclosures of PHI; patient rights over their information |
| **Security Rule** | Administrative, physical, and technical safeguards for ePHI |
| **Breach Notification Rule** | Requirements to notify individuals, HHS, and media when ePHI is breached |

**Key technical safeguards:** Access controls (unique user identification, emergency access procedures), audit controls, integrity controls, transmission security (encryption for data in transit).

**Penalties:** Tiered from $100 to $50,000 per violation, up to $1.9 million per violation category per year. Criminal penalties apply for intentional violations.

### PCI-DSS (Payment Card Industry Data Security Standard)

**Who it applies to:** Any organization that stores, processes, or transmits payment card data -- merchants, payment processors, service providers, and their vendors.

PCI-DSS is maintained by the Payment Card Industry Security Standards Council (a consortium of Visa, Mastercard, American Express, Discover, and JCB) and is contractually required by card network agreements rather than law.[5]

**The 12 requirements (PCI-DSS v4.0, 2022):**

| Domain | Requirements |
|---|---|
| Network security | Build and maintain a secure network; install firewalls; change vendor default passwords |
| Cardholder data | Protect stored cardholder data; encrypt transmission over public networks |
| Vulnerability management | Use anti-malware; maintain secure systems and software |
| Access control | Restrict access to cardholder data; authenticate access; restrict physical access |
| Monitoring | Log and monitor access; test security systems regularly |
| Policy | Maintain an information security policy |

Non-compliance consequences: fines from card networks ($5,000 to $100,000/month), increased transaction fees, and ultimately loss of the ability to accept card payments.

### SOC 2 (System and Organization Controls 2)

**Who it applies to:** Technology and cloud service providers that store or process customer data. SOC 2 is not a regulation but a voluntary attestation widely required as a condition of doing business.

SOC 2 audits are conducted by licensed CPA firms against the AICPA Trust Services Criteria, which cover five categories: Security, Availability, Processing Integrity, Confidentiality, and Privacy. Organizations select which categories apply to their services.[6]

| Report Type | What It Proves |
|---|---|
| **SOC 2 Type I** | Controls are designed appropriately (a point-in-time assessment) |
| **SOC 2 Type II** | Controls operated effectively over a defined period (typically 6-12 months) |

Type II reports are the meaningful standard. A Type I report only proves that controls exist on paper on a specific day. A Type II report proves they actually operated consistently.

SOC 2 is the de facto standard for SaaS companies selling to enterprise customers. Enterprise procurement teams require it before approving vendors who will process their data.

### ISO/IEC 27001

**Who it applies to:** Any organization, any size, any sector. ISO 27001 is the international standard for information security management systems (ISMS).

Unlike most compliance frameworks, ISO 27001 does not mandate a specific list of controls. It mandates a management system: a risk-based, continuously improving cycle of planning, implementing, monitoring, and improving information security.[7] Organizations assess their risks and select controls from Annex A (93 controls across 11 domains in the 2022 edition) proportionate to those risks.

Certification is awarded by accredited certification bodies after a two-stage audit: a documentation review and an on-site assessment. Certification must be maintained through annual surveillance audits and a full recertification every three years.

**Why it matters:** ISO 27001 certification is increasingly required in European government and enterprise procurement, and is a credible signal of security maturity globally.

### CMMC (Cybersecurity Maturity Model Certification)

**Who it applies to:** US Department of Defense contractors and subcontractors handling Controlled Unclassified Information (CUI).

CMMC 2.0 (released 2021) establishes three maturity levels, with Level 2 requiring an independent third-party assessment against NIST SP 800-171's 110 security requirements. CMMC is not optional for DoD contractors -- it will be a contract requirement, and organizations without the appropriate CMMC level will be ineligible for DoD contracts.[8]

### FedRAMP (Federal Risk and Authorization Management Program)

**Who it applies to:** Cloud service providers seeking to sell to US federal agencies.

FedRAMP standardizes cloud security assessment, authorization, and monitoring for federal systems. It is based on NIST SP 800-53 controls, with three impact levels (Low, Moderate, High) determining which control set applies. Authorization requires a significant investment: third-party assessment organization (3PAO) audit, agency sponsorship, and ongoing continuous monitoring.[9]

---

## The Compliance Lifecycle

Compliance is not a project with a completion date. It is an ongoing cycle.

```
Assess → Plan → Implement → Audit → Certify → Monitor → Assess (again)
```

**Assess:** Determine which regulations and frameworks apply. Conduct a gap assessment against each applicable standard to understand current state vs. required state.

**Plan:** Develop a remediation roadmap. Prioritize gaps by risk and compliance deadline. Assign ownership and timelines.

**Implement:** Deploy the required controls -- technical, administrative, and physical. Document everything. Evidence is the currency of compliance.

**Audit:** Internal auditors verify controls are implemented and operating. Findings are documented and remediated. For certifiable standards (ISO 27001, SOC 2, CMMC), external auditors conduct formal assessments.

**Certify:** Formal certification or attestation is issued. For regulations like GDPR and HIPAA, there is no certification -- compliance is an ongoing obligation enforced by regulators.

**Monitor:** Compliance does not hold itself. Controls drift. Regulations change. New systems are deployed that are not in scope. Continuous monitoring -- including automated compliance tools, regular internal audits, and management reviews -- maintains the certified state.

{% hint style="warning" %}
**The gap between certification and compliance:** ISO 27001 certification is valid for three years with annual surveillance audits. A system deployed the day after a certification audit has three years of potential drift before the next full audit. Organizations that treat certification as a finish line rather than a waypoint accumulate compliance debt that surfaces dramatically during the next audit or, worse, during a breach investigation.
{% endhint %}

---

## Evidence Management

Compliance lives and dies on documentation. Every control must be evidenced -- not just stated to exist, but demonstrated to be operating.

Evidence types include:

- **Policies and procedures**: Written documents defining what must happen
- **Configuration screenshots**: System settings showing controls are enabled
- **Log exports**: Records of activity demonstrating controls operated
- **Training completion records**: Evidence that staff received required training
- **Risk assessment documents**: Documented evidence of the risk assessment process
- **Vendor assessments**: Evidence of third-party security evaluation
- **Penetration test reports**: Evidence of technical security testing
- **Audit reports**: Results of internal and external audits with findings and remediation

Evidence must be:
- Current (not from three years ago)
- Complete (covering the full scope, not selected systems)
- Authentic (not modified)
- Accessible (retrievable when auditors request it)

GRC platforms -- Vanta, Drata, Tugboat Logic, OneTrust, ServiceNow GRC -- automate evidence collection by integrating with cloud platforms, identity providers, and security tools to pull compliance evidence continuously rather than in manual point-in-time snapshots.

---

## Multi-Framework Compliance

Most organizations are subject to multiple frameworks simultaneously. A US healthcare SaaS company might need HIPAA, SOC 2, ISO 27001, and GDPR at the same time.

The practical approach is to map frameworks against each other to identify overlap. Most frameworks share common control objectives:

{% hint style="success" %}
**Controls that satisfy multiple frameworks simultaneously:**
- **MFA on all accounts**: satisfies GDPR Article 32, HIPAA technical safeguards, PCI-DSS Req 8, ISO 27001 A.9, SOC 2 CC6.1
- **Encryption in transit and at rest**: satisfies GDPR, HIPAA, PCI-DSS, ISO 27001, SOC 2
- **Access reviews (quarterly)**: satisfies HIPAA, PCI-DSS, ISO 27001, SOC 2
- **Security awareness training**: satisfies HIPAA, PCI-DSS, ISO 27001, SOC 2, CMMC

Implementing controls correctly once and mapping them to all applicable frameworks is far more efficient than implementing separate control sets per framework. This is the foundation of an integrated compliance program.
{% endhint %}

---

## Third-Party and Supply Chain Compliance

An organization's compliance obligations extend to vendors and suppliers that handle their regulated data. GDPR requires Data Processing Agreements with all processors of EU personal data. HIPAA requires Business Associate Agreements with all parties handling PHI. PCI-DSS requires ensuring that third-party service providers also comply with applicable requirements.

Third-party compliance management involves:

- Maintaining a vendor inventory (who has access to what data)
- Executing required legal agreements (DPAs, BAAs)
- Assessing vendor compliance posture (questionnaires, certifications, right-to-audit)
- Monitoring vendor compliance on an ongoing basis
- Defining processes for vendor incidents (what happens when a vendor is breached)

The 2023 MOVEit breach, in which the Cl0p ransomware group exploited a SQL injection zero-day, illustrates the supply chain compliance challenge: hundreds of organizations discovered they were indirectly affected because their vendors used MOVEit Transfer for file sharing. The downstream data exposure triggered GDPR, HIPAA, and state breach notification obligations for organizations that had no direct relationship with MOVEit.[10]

---

## Compliance as a Career

Compliance and GRC roles are among the most stable and well-compensated non-technical positions in cybersecurity. Organizations subject to multiple frameworks need dedicated compliance professionals who understand both the regulatory landscape and the technical controls that satisfy it.

**Common roles:**
- Compliance Analyst: managing evidence collection, audit preparation, policy maintenance
- GRC Manager: overseeing multiple frameworks, managing assessments, reporting to leadership
- Data Protection Officer (DPO): legally mandated role under GDPR for certain organizations
- Virtual CISO (vCISO): fractional senior security and compliance leadership across multiple clients
- Audit Manager: leading internal or external compliance audits

**Skills that matter:**
- Deep knowledge of 2-3 primary frameworks relevant to your industry
- Familiarity with GRC platforms (Vanta, Drata, OneTrust, ServiceNow)
- Evidence management and audit preparation experience
- Clear written communication for policy development and executive reporting
- Ability to translate regulatory requirements into technical control specifications

---

## References

[1] Information Commissioner's Office. (2020). *ICO fines British Airways £20 million for data breach affecting more than 400,000 customers*. ICO. Retrieved from https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2020/10/ico-fines-british-airways-20million-for-data-breach-affecting-more-than-400-000-customers/

[2] European Parliament and Council of the European Union. (2016). Regulation (EU) 2016/679 -- General Data Protection Regulation. *Official Journal of the European Union*, L 119, 1--88. Retrieved from https://gdpr-info.eu

[3] Data Protection Commission Ireland. (2023). *Decision of the Data Protection Commission: Meta Platforms Ireland Limited*. DPC. Retrieved from https://www.dataprotection.ie/en/dpc-guidance/decision-meta-platforms-ireland-limited

[4] US Department of Health and Human Services. (2003). Security Standards for the Protection of Electronic Protected Health Information. *Federal Register*, 68(34), 8333--8381. Retrieved from https://www.hhs.gov/hipaa/for-professionals/security/index.html

[5] PCI Security Standards Council. (2022). *Payment Card Industry Data Security Standard Requirements and Testing Procedures, Version 4.0*. PCI SSC. Retrieved from https://www.pcisecuritystandards.org

[6] American Institute of CPAs. (2017). *Trust Services Criteria for Security, Availability, Processing Integrity, Confidentiality, and Privacy (SOC 2)*. AICPA. Retrieved from https://www.aicpa.org/resources/download/2017-trust-services-criteria-for-security-availability-processing-integrity-confidentiality-and-privacy

[7] International Organization for Standardization. (2022). *ISO/IEC 27001:2022 -- Information Security Management Systems -- Requirements*. ISO/IEC JTC 1/SC 27.

[8] US Department of Defense. (2021). *Cybersecurity Maturity Model Certification (CMMC) 2.0*. Office of the Under Secretary of Defense for Acquisition and Sustainment. Retrieved from https://www.acq.osd.mil/cmmc/

[9] General Services Administration. (2023). *FedRAMP Authorization Act Implementation Guidance*. Federal Risk and Authorization Management Program. Retrieved from https://www.fedramp.gov

[10] Cybersecurity and Infrastructure Security Agency. (2023). *#StopRansomware: CL0P Ransomware Gang Exploits CVE-2023-34362 MOVEit Vulnerability*. CISA Advisory AA23-158A. Retrieved from https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-158a

---

## Further Reading

| Resource | What It Covers |
|---|---|
| [GDPR Full Text](https://gdpr-info.eu) | Clean, searchable GDPR with articles and recitals. Essential reference for data protection work. |
| [HHS HIPAA](https://www.hhs.gov/hipaa) | Official source for HIPAA rules, guidance, and enforcement actions. |
| [PCI DSS v4.0](https://www.pcisecuritystandards.org) | Current PCI-DSS standard and supporting guidance documents. |
| [ISO 27001:2022](https://www.iso.org/standard/27001) | The international ISMS certification standard. |
| [FedRAMP](https://www.fedramp.gov) | US federal cloud authorization program documentation and approved provider list. |
| [Vanta](https://www.vanta.com) / [Drata](https://drata.com) | Leading GRC automation platforms; both offer free resources and compliance guides. |

---

*Questions about compliance frameworks, GRC career paths, or audit preparation? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back -- this book is open source and your additions are welcome.*
