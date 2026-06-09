# Governance

## The Difference Between Governance and Management

In 2017, Equifax's board of directors learned that attackers had been inside their network for 78 days. The breach had begun in May. It was discovered in July. It was disclosed to the public in September. 147 million people had their Social Security numbers, birth dates, and addresses exposed.

The technical failure was a known, unpatched vulnerability. But the deeper failure was structural: nobody with real authority had been asking the hard questions about whether security controls were actually working. The security team reported to the CIO. The CIO reported to the CEO. The board received no regular security briefings. There was no independent oversight. Governance had failed before the first packet crossed the network.[1]

This is what governance failure looks like in practice. Not a missed alert. A missing accountability structure.

Understanding the difference between governance and management is where this chapter begins, because they are genuinely different things and the confusion between them causes real harm.

**Governance** sets the direction. It answers: What are we trying to protect? Who is authorized to make decisions? How do we know the right things are happening? Governance is exercised by boards, executives, and oversight committees. It is about accountability and assurance.

**Management** executes the direction. It answers: How do we implement the controls? What specific actions do we take? How do we respond to this incident? Management is exercised by CISOs, security teams, and operational staff. It is about implementation and operations.

Governance without management produces policies that exist but are not implemented. Management without governance produces activity without direction, accountability, or alignment to what the organization actually needs to protect.[2]

{% hint style="info" %}
**The one-sentence version:**

Governance = doing the right things.
Management = doing things right.

Both are necessary. Neither substitutes for the other.
{% endhint %}

---

## Why Governance Exists: The Legal Reality

Governance in information security is not just a best practice. In many contexts it is a legal obligation.

Directors and senior executives owe a **duty of care** to their organizations. In corporate law, this means they must act with the care, competence, and diligence that a reasonably prudent person in a similar position would exercise.[3] This duty extends to cybersecurity. A board that pays no attention to security, provides no resources, and receives no reporting on security posture cannot claim ignorance as a defense when a breach results in regulatory action, shareholder lawsuits, or criminal liability.

The regulatory landscape makes this explicit:

- **GDPR** requires that boards ensure appropriate technical and organizational measures are in place. Data Protection Officers report to the highest management level.
- **SEC regulations** (effective 2023) require public companies to disclose material cybersecurity incidents within four business days and to report annually on the board's cybersecurity expertise and oversight processes.[4]
- **HIPAA** creates personal liability for covered entity executives who fail to implement required security safeguards.
- **UK Corporate Governance Code** explicitly addresses board responsibility for risk management, which regulators have interpreted to include cyber risk.

The consequence: information security governance is now a matter of corporate law, not just IT policy. Boards that treat it as a technical issue to be delegated entirely to IT are exposed.

---

## The CISO Role

The Chief Information Security Officer is the executive responsible for developing and maintaining the organization's information security program. The CISO sits at the intersection of governance and management, reporting to senior leadership on security posture while directing the operational security function.

{% hint style="info" %}
**Where the CISO reports matters enormously.**

A CISO who reports to the CIO faces an inherent conflict: the CIO is evaluated partly on system availability and project delivery, which security controls can slow. A CISO who reports to the CEO or directly to the board has independent authority and visibility that enables genuine oversight.

Industry best practice, reflected in frameworks like NIST and ISO 27001, is that the CISO should have a direct reporting line to the board or audit committee, with a separate administrative reporting line to the CEO or COO. This separation preserves independence.[5]
{% endhint %}

In smaller organizations, the CISO function may be fulfilled by a Director of IT Security, a Security Manager, or even outsourced to a virtual CISO (vCISO), a consultant who provides part-time CISO-level guidance. The function matters more than the title.

A related role has been splitting off in larger and more regulated organizations: the **Chief Privacy Officer (CPO)**. Where the CISO owns the security of information, the CPO owns how personal data is collected, used, and protected in line with privacy law (GDPR, CCPA/CPRA, and the growing US state patchwork). The two roles overlap heavily and must work closely, but the rise of privacy regulation has made them distinct accountabilities rather than one person's side responsibility.

**Primary CISO responsibilities:**

- Developing and maintaining the information security strategy
- Overseeing risk management and risk assessment processes
- Developing and enforcing security policies
- Managing security incident response
- Reporting to the board and executive leadership on security posture
- Ensuring compliance with applicable regulations
- Building and managing the security team
- Managing relationships with external auditors and regulators

CISO tenure has historically been short — older surveys put it around 18 to 26 months, well below other C-suite roles. More recent surveys (Hitch Partners' 2025 leadership survey reported an average of around 39 months) suggest tenures are lengthening as the role matures and gains genuine board access, though figures vary widely by company size and survey methodology, and tenure at small companies remains notably shorter. Either way, the underlying pressures persist: high accountability, limited authority in many organizations, and constant pressure from both attackers and the business make burnout common. The professionals who last longest are typically those who have built strong executive relationships and have the organizational standing to actually implement the programs they design.

---

## Governance Frameworks

Several frameworks provide structured approaches to information security governance. You do not need to know all of them in depth, but you need to know what they are, what problem each solves, and where each is most commonly used.

### COBIT (Control Objectives for Information and Related Technology)

Developed by ISACA, COBIT is the most comprehensive governance framework for IT and information security. It defines governance objectives, management objectives, and the relationships between them across five domains: Evaluate, Direct, and Monitor (governance) and Align, Plan and Organize, Build, Acquire and Implement, Deliver, Service and Support, and Monitor, Evaluate and Assess (management).[7]

COBIT 2019 (the current version) is particularly strong on the governance side: it defines how boards should direct IT strategy, how objectives cascade from governance to management, and how performance should be measured. It is most commonly used in larger enterprises and public sector organizations with mature governance structures.

### ISO/IEC 27001

ISO 27001 is the international standard for information security management systems (ISMS). An ISMS is the collection of policies, processes, and controls an organization uses to manage information security systematically.

Certification to ISO 27001 is a public statement that an independent auditor has verified your information security management meets the standard's requirements. It is increasingly required as a condition of doing business, particularly in enterprise B2B sales, government contracting, and working with European organizations under GDPR.[8]

ISO 27001 does not prescribe specific technical controls. It prescribes a management system: a cycle of planning, implementing, monitoring, and improving information security. Annex A of the standard provides 93 control objectives across 11 domains (ISO 27001:2022 version) from which organizations select those relevant to their risk profile.

{% hint style="info" %}
**Free ISO 27001 implementation toolkit:** The [ISO27k Toolkit](https://www.iso27001security.com/html/iso27k_toolkit.html) is a community-maintained collection of free policy templates, procedure documents, Statement of Applicability worksheets, and governance artifacts — everything you need to begin an ISO 27001 implementation without starting from a blank page.
{% endhint %}

### NIST Cybersecurity Framework (CSF)

The NIST CSF was originally developed for US critical infrastructure but has become the most widely adopted voluntary cybersecurity framework globally. It organizes security activities into six functions: Govern, Identify, Protect, Detect, Respond, and Recover.[9]

CSF 2.0 (released in 2024) added "Govern" as an explicit function, reflecting the industry recognition that governance cannot be separated from technical security. The Govern function addresses organizational context, risk management strategy, roles and responsibilities, policy, and supply chain risk.

{% hint style="info" %}
**Migrating from CSF 1.1 to 2.0?** The five original functions (Identify, Protect, Detect, Respond, Recover) are unchanged in substance — your existing mappings still apply. Three things changed. First, **Govern** was added as a sixth function that sits across all the others: organizational context, risk strategy, roles, policy, and oversight that were previously scattered (mostly inside Identify) now have an explicit home. Second, **supply chain risk management** was elevated and made far more prominent. Third, the framework's scope is now explicitly *all* organizations, not just critical infrastructure. In practice, migration mostly means re-homing your governance-related controls under Govern and giving supply chain risk the attention 2.0 expects — not redoing your whole program.
{% endhint %}

The CSF is not certifiable (unlike ISO 27001), but it is used by US federal agencies, large enterprises, and SMBs alike as a communication tool, helping executives, boards, and technical teams share a common language for discussing security posture.

{% hint style="info" %}
**NIST CSF 2.0 tools:** The full framework, including a reference tool and downloadable Excel profile templates, is free at [nist.gov/cyberframework](https://www.nist.gov/cyberframework). The Excel workbook lets you record your organization's current and target tier for each subcategory and generate a gap report — a practical starting point for any governance roadmap.
{% endhint %}

### A Practical Comparison

| Framework | Best For | Certifiable? | Primary Focus |
|---|---|---|---|
| **COBIT 2019** | Large enterprises; IT governance | No (though assessments exist) | Governance structure and IT alignment |
| **ISO 27001** | Any size; required in many sectors | Yes | Information security management system |
| **NIST CSF** | US organizations; communication | No | Security function maturity and posture |
| **NIST 800-53** | US federal agencies and contractors | Used as FedRAMP basis | Comprehensive security controls catalog |
| **SOC 2** | SaaS and cloud service providers | Yes (Type I and II) | Trust service criteria for customer assurance |

---

## The Board's Role

Boards of directors are ultimately responsible for the organizations they oversee, including their security posture. This is not just theoretical. Regulators, courts, and shareholders have made it concrete.

What good board-level security governance looks like:

{% hint style="success" %}
**Signs of effective board governance:**
- The board receives regular security briefings (at least quarterly) covering current threat landscape, security posture metrics, and significant incidents
- At least one board member has meaningful cybersecurity expertise, either through a dedicated seat or a committee with external advisors
- The CISO has direct access to the board, not only access filtered through the CIO or CEO
- The board approves the information security strategy and risk appetite
- Security is a standing agenda item, not a one-time presentation after a breach
- Board members can articulate what the organization's most significant cyber risks are
{% endhint %}

{% hint style="warning" %}
**Signs of governance failure:**
- Security is only discussed at the board when something goes wrong
- The board cannot distinguish between security posture and IT operations
- The CISO has never met with the board directly
- There is no approved written risk appetite statement for information security
- Security budget decisions are made entirely by IT without board input or oversight
{% endhint %}

The National Association of Corporate Directors (NACD) publishes a Cyber-Risk Oversight Handbook specifically for board members.[10] It is worth reading even from a practitioner standpoint, because understanding what good governance looks like at the board level shapes what good governance looks like at every level below it.

---

## Building an Information Security Governance Framework

For organizations building a governance framework from scratch, or practitioners advising clients who need one, the process follows a consistent structure.

### Step 1: Identify What Applies to You

Start with compliance and contractual obligations. The governance framework must, at minimum, satisfy what is legally required.

Questions to ask:
- Which data protection regulations apply? (GDPR, HIPAA, CCPA, PCI-DSS, sector-specific rules)
- Are there contractual requirements from customers or partners? (SOC 2 reports, ISO 27001 certification)
- Are there government contracting requirements? (FedRAMP, CMMC, NIST 800-171)
- Are there sector-specific requirements? (NERC CIP for energy, FFIEC for financial services)

### Step 2: Define Risk Appetite

Risk appetite is the amount and type of risk an organization is willing to accept in pursuit of its objectives. It must be defined explicitly and approved at the board or senior executive level, because all subsequent risk management decisions are made against it.

An organization that has never articulated its risk appetite is implicitly accepting whatever risk exists. That is not governance. It is abdication.

### Step 3: Establish Roles and Responsibilities

Define who is responsible for what, with enough specificity to be enforceable:

| Role | Governance Responsibility |
|---|---|
| Board / Audit Committee | Oversight; approves risk appetite and security strategy; receives regular reporting |
| CEO / COO | Accountable for security program at the executive level |
| CISO | Develops and manages the security program; reports to board and executives |
| Business Unit Managers | Responsible for security within their functions; data asset owners |
| Security Team | Implements and operates controls; monitors and responds to incidents |
| All Employees | Comply with policies; report security concerns |

### Step 4: Develop and Enforce Policies

Policies are the formal expression of governance decisions. A complete policy framework covers at minimum:

- Information Security Policy (the overarching statement)
- Acceptable Use Policy
- Access Control Policy
- Incident Response Policy
- Data Classification and Handling Policy
- Business Continuity and Disaster Recovery Policy
- Vendor and Third-Party Risk Policy

A governance responsibility that has become explicit since CSF 2.0 and a wave of supply-chain attacks: knowing what software your organization actually runs. A **Software Bill of Materials (SBOM)** — a machine-readable inventory of the components and dependencies inside a piece of software — has moved from best practice toward expectation, driven in the US by Executive Order 14028 and its follow-on guidance. Governance doesn't generate SBOMs (that's a DevSecOps task, covered in Chapter 10), but it owns the *requirement*: deciding that vendors must provide one, that internal builds must produce one, and that someone is accountable for acting on what they reveal.

Policies must be communicated, acknowledged, enforced uniformly, and reviewed regularly. A policy that exists only as a PDF on a shared drive is not a control.

{% hint style="success" %}
**Free policy templates — no need to start from scratch:** The [SANS Information Security Policy Templates](https://www.sans.org/information-security-policy/) library provides 27 peer-reviewed, customizable policy documents. Acceptable Use, Password Policy, Incident Response, Data Classification, and more — written to professional standard and ready to adapt. Download, modify for your context, get legal review, and publish.
{% endhint %}

### Step 5: Implement Measurement and Reporting

You cannot govern what you cannot measure. The CISO should report to the board on metrics that reflect actual security posture, not just activities:

- Mean time to detect (MTTD) and mean time to respond (MTTR) to incidents
- Patch compliance rate (percentage of systems patched within SLA)
- Phishing simulation click rate (and trend over time)
- Vulnerability management metrics (open critical vulnerabilities by age)
- Security awareness training completion rates
- Third-party risk assessment coverage

Metrics should tell a story, not fill a slide. The question is always: is our security posture improving, holding steady, or declining?

---

## Governance as a Career

For professionals interested in GRC as a career path, governance is where the most senior and well-compensated roles in non-technical security live. A CISO at a large enterprise can earn $300,000 to $500,000. Virtual CISOs advising multiple organizations earn $200,000 to $400,000 across their client portfolios. Even mid-level GRC analysts and compliance managers earn $90,000 to $150,000.

The skills that matter most are not technical:
- The ability to translate complex risk into business language that a CFO or board member can act on
- Deep knowledge of the regulatory landscape relevant to your industry
- Experience with audit processes and evidence management
- Strong written communication for policy development and executive reporting
- Organizational credibility and relationship-building

The certifications most relevant to governance roles are CISM (Certified Information Security Manager), CRISC (Certified in Risk and Information Systems Control), and CISSP (for senior generalist roles). ISACA's certifications dominate this space.[11]

---

## Templates and Examples You Can Use Today

Reading about governance is useful. Having ready-made templates to build from is better. These resources are free, maintained by authoritative sources, and used by practitioners worldwide.

| Resource | What You Get | Best For |
|---|---|---|
| [SANS Information Security Policy Templates](https://www.sans.org/information-security-policy/) | 27 peer-reviewed, customizable policy documents: Acceptable Use, Password Policy, Incident Response, Data Classification, and more | Starting a policy library from scratch; updating existing policies to professional standard |
| [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework) | Free framework PDF, Excel workbook for current/target profile tracking, and reference implementation examples | Communicating security posture to executives and boards; building a governance roadmap |
| [CIS Controls v8](https://www.cisecurity.org/controls) | Free implementation guide and Excel mapping spreadsheet cross-referencing NIST CSF, ISO 27001, and PCI-DSS | Translating governance objectives into specific technical controls; showing coverage across frameworks |
| [NIST Privacy Framework](https://www.nist.gov/privacy-framework) | Free privacy-governance companion framework with profiles and implementation guides | Organizations subject to GDPR, CCPA, or HIPAA needing a structured approach to privacy governance |
| [ISO27k Toolkit](https://www.iso27001security.com/html/iso27k_toolkit.html) | Community-contributed ISO 27001 policy templates, procedure documents, governance artifacts, and management review materials | ISO 27001 preparation; building governance documentation without starting from a blank page |

{% hint style="info" %}
**A practical governance starter pack:** Download the SANS policy templates for your immediate policy needs. Use the NIST CSF 2.0 Excel workbook to map your current and target security posture across all six functions. Pull the ISO27k Toolkit templates if you are working toward ISO 27001 certification. None of these require registration or payment. They represent decades of collective practitioner knowledge built into a usable form.
{% endhint %}

---

## Try This

1. **Run a one-function gap assessment.** Download the free [NIST CSF 2.0](https://www.nist.gov/cyberframework) reference material and pick the **Govern** function. For an organization you know (your employer, a club, even your own household IT), rate each Govern subcategory as Not Started / Partial / Done, and write one sentence on the biggest gap. You've just produced the core artifact of a governance roadmap — and felt why "we have antivirus" is not the same as "we govern security."
2. **Adapt a real policy.** Open the [SANS Acceptable Use Policy template](https://www.sans.org/information-security-policy/) and tailor it to a small fictional company in 30 minutes: name, scope, what's allowed, consequences. Notice how much of governance is clear writing and explicit decisions, not technology. This is exactly the work an entry-level GRC analyst does, and a tailored policy is portfolio material.

---

## Key Takeaways

- Governance (doing the right things) and management (doing things right) are distinct. Most catastrophic failures, like Equifax, are governance failures — a missing accountability structure, not a missed alert.
- Security governance is now corporate law, not IT policy: duty of care, SEC disclosure rules, and personal executive liability all apply.
- Where the CISO reports determines whether oversight is real. Independence from the CIO is the structural ideal; the CPO is increasingly a separate accountability.
- Know the frameworks by purpose: COBIT (governance structure), ISO 27001 (certifiable management system), NIST CSF 2.0 (posture and communication, now with a Govern function and supply-chain emphasis), SOC 2 (customer assurance).
- Governance owns the *requirements* — risk appetite, policies, SBOM expectations, and metrics that measure posture rather than activity.

---

## References

[1] Federal Trade Commission. (2019). *Equifax Data Breach Settlement*. FTC. Retrieved from https://www.ftc.gov/enforcement/refunds/equifax-data-breach-settlement

[2] International Organization for Standardization. (2015). *ISO/IEC 38500:2015 -- Information Technology -- Governance of IT for the Organization*. ISO. Retrieved from https://www.iso.org/standard/62816.html

[3] American Bar Association. (2023). *Model Business Corporation Act* (4th ed.). ABA Business Law Section. Section 8.30 (Standards of Conduct for Directors).

[4] US Securities and Exchange Commission. (2023). *Cybersecurity Risk Management, Strategy, Governance, and Incident Disclosure*. 17 CFR Parts 229, 232, 239, and 249. Federal Register. doi:10.17487/SEC-2023-cybersecurity

[5] National Institute of Standards and Technology. (2018). *Framework for Improving Critical Infrastructure Cybersecurity, Version 1.1*. NIST. doi:10.6028/NIST.CSWP.04162018

[6] Hitch Partners. (2025). *2025 CISO Security Leadership Survey Results*. Hitch Partners. Retrieved from https://www.hitchpartners.com/ciso-security-leadership-survey-results-25 (reports average current CISO tenure of ~39 months; earlier industry surveys cited 18-26 months)

[7] ISACA. (2018). *COBIT 2019 Framework: Governance and Management Objectives*. ISACA. ISBN 978-1-60420-763-2.

[8] International Organization for Standardization. (2022). *ISO/IEC 27001:2022 -- Information Security, Cybersecurity and Privacy Protection -- Information Security Management Systems -- Requirements*. ISO/IEC JTC 1/SC 27.

[9] National Institute of Standards and Technology. (2024). *The NIST Cybersecurity Framework 2.0*. NIST. doi:10.6028/NIST.CSWP.29

[10] National Association of Corporate Directors. (2023). *NACD Director's Handbook on Cyber-Risk Oversight*. NACD. Retrieved from https://www.nacdonline.org/insights/publications.cfm?ItemNumber=67298

[11] ISACA. (2024). *CISM Certification*. ISACA. Retrieved from https://www.isaca.org/credentialing/cism

---

## Further Reading

| Resource | What It Covers |
|---|---|
| [NIST CSF 2.0](https://www.nist.gov/cyberframework) | The current cybersecurity framework with the new Govern function. Free, well-structured, widely used. |
| [ISO 27001:2022](https://www.iso.org/standard/27001) | The international ISMS standard. Purchase required, but summaries are freely available. |
| [ISACA COBIT](https://www.isaca.org/resources/cobit) | The comprehensive IT governance framework. Free resources available with ISACA membership. |
| [SEC Cyber Disclosure Rules](https://www.sec.gov/rules/final/2023/33-11216.pdf) | The 2023 rules requiring public companies to disclose material incidents and board oversight processes. |
| [NACD Cyber-Risk Oversight Handbook](https://www.nacdonline.org) | Written for board members; useful for practitioners who want to understand what boards should be asking. |

---

*Questions about governance, GRC careers, or where to start with compliance frameworks? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back. This book is open source and your additions are welcome.*
