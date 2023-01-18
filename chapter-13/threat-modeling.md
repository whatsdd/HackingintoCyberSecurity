# Threat Modeling

### **Threat Modeling** <a href="#_q6d96uvc57u8" id="_q6d96uvc57u8"></a>

### Introduction <a href="#_19r0n5nq3khu" id="_19r0n5nq3khu"></a>

Threat modeling is a structured approach to identifying and mitigating potential security threats to a system, network or application. It involves analyzing the system's architecture, data flows, and potential attack vectors to identify potential vulnerabilities and the impact of those vulnerabilities. This can include identifying the assets that need to be protected, the threats that could be used to exploit those assets, and the vulnerabilities that could be exploited. Once the potential vulnerabilities have been identified, a risk assessment can be performed to determine the likelihood and impact of each threat, and then mitigation strategies can be developed to address the most significant risks.

The process of threat modeling typically involves several steps, including:

* Identifying assets and determining their value.
* Identifying potential threats and attack vectors.
* Identifying potential vulnerabilities and attack surfaces.
* Conducting a risk assessment to determine the likelihood and impact of each threat.
* Developing and implementing mitigation strategies to address the most significant risks.
* Continuously monitoring and updating the threat model to account for new threats and vulnerabilities.

It's important to note that threat modeling is an iterative process, and it should be performed regularly to ensure that the system, network, or application remains secure. And it's also important to involve different teams in the process, such as developers, security professionals, and business stakeholders, as they may have different perspectives and insights that can help identify potential vulnerabilities.

### Threat modeling overview <a href="#_uc2w7omlecru" id="_uc2w7omlecru"></a>

Threat modeling is a crucial step in identifying and mitigating potential security threats in an organization's systems or software. It involves walking through a structured process to identify all potential security risks, evaluate their severity, and prioritize them for mitigation. This approach helps organizations to proactively address potential vulnerabilities, rather than waiting for an incident to occur. It also allows organizations to develop a deeper understanding of their systems, which can aid in the early detection and prevention of security issues, resulting in lower costs for remediation and incident response.

### The threat modeling process <a href="#_lkxcii45w1up" id="_lkxcii45w1up"></a>

As every organization, system and security team is unique, there are a variety of threat modeling methodologies that can be employed to meet their particular needs and goals. While each has their own slightly different naming convention and series of steps, the most prevalent threat models processes encompass roughly the same logical flow at their core.These steps typically include:

* Identify assets: Understand what you're trying to protect, including data, systems, and users.
* Identify threats: Understand who might want to attack your assets and why.&#x20;
* Identify vulnerabilities: Understand how the threats might exploit the assets.
* Evaluate the risks: Assess the likelihood of each threat exploiting each vulnerability.
* Mitigate the risks: Implement countermeasures to reduce the likelihood or impact of the risks.
* Monitor and update: Continuously monitor the system for new threats and vulnerabilities and update the threat model accordingly.

It's important to note that threat modeling is an ongoing process and not a one-time event. As technology and business requirements change, so too should the threat model be updated to reflect new risks and vulnerabilities. Additionally, threat modeling should be integrated into the development life cycle and not seen as a separate step.

### Main threat modeling frameworks <a href="#_3ymj79xofkxa" id="_3ymj79xofkxa"></a>

While a complete breakdown of each of the main threat modeling frameworks is not within the scope of this article, the models introduced below represent ten of the most prevalent. As with other types of risk modeling, quantitative and qualitative analysis combine to demonstrate that threat modeling is still in many ways an art as opposed to a pure scientific process.

**Attack Trees**

Attack trees are a valuable tool for organizations looking to document and address cyber risk. First introduced by Bruce Schneier in the late 1990s, these logic models provide a visual and methodological approach for describing systems and assessing various aspects of an attack surface.

![](<../.gitbook/assets/0 (2)>)

To construct an attack tree, organizations typically follow these six steps:

1. Identify the assets that need protection
2. Identify potential threats to those assets
3. Understand the nature of those threats
4. Categorize the threats based on their characteristics
5. Evaluate the likelihood of each threat
6. Identify mitigation strategies or defensive measures to address the threats

By using an attack tree, organizations can make informed decisions, identify vulnerable systems and evaluate the likelihood of certain attack vectors.

**STRIDE**

The STRIDE model is a well-established method for conducting cyber threat modeling. Developed by Microsoft employees Loren Kohnfleder and Praerit Garg in 1999, the model is built around the CIA triad (Confidentiality, Integrity, and Availability) and is an acronym that represents the six types of threats:

* Spoofing
* Tampering
* Repudiation
* Information disclosure
* Denial of service
* Elevation of privilege

![](<../.gitbook/assets/1 (4)>)

The STRIDE methodology aligns with Microsoft's Trustworthy Computing initiative and is designed to provide software developers with the tools needed to integrate security into the software design phase. The process starts with security professionals creating a data flow diagram that identifies the system's components, events, interactions, and boundaries. They then overlay this diagram with a general set of known threats using the threat types identified by STRIDE.

As deviations or issues are identified in the system when compared to the STRIDE model, developers can then refine the target system. This process continues until all threats are addressed or the organization reaches its defined level of acceptable risk.

**OCTAVE**

The OCTAVE threat modeling methodology, developed by Carnegie Mellon University’s Software Engineering Institute (SEI) and CERT in 2003, provides an enterprise-level perspective of cyber risk. Unlike other threat modeling methods, OCTAVE focuses on organization-level risks, such as the impact of breaches of proprietary or customer data, instead of only assessing technology threats. The acronym stands for Operational Critical Threat, Asset and Vulnerability Evaluation.

Organizations using the OCTAVE model move through three phases:

Asset identification: All assets involved in storing, processing, and transferring information across the organization, as well as the associated datasets, are captured and attributes are assigned based on the type and sensitivity of the data. Technical component documentation: Specific technical components and their associated vulnerabilities are documented. Evaluation, strategy development, and decision making: The information from Phase 1 and Phase 2 are evaluated, a security strategy and required resources are developed and identified. Decisions to address or take action on them can be made by organizational leadership. OCTAVE allows organizations to identify and prioritize assets and threats, and to develop a risk management strategy that aligns with their specific business needs.

![](<../.gitbook/assets/2 (1)>)

**MITRE**

The MITRE Adversary Tactics Techniques and Common Knowledge (ATT\&CK) framework is a well-known method for identifying, cataloging and understanding organizational vulnerabilities and cyber attack methods. Launched in 2015, it has quickly become a widely used tool in the industry. The framework is divided into 11 tactics, each further populated with a range of techniques that attackers could use, totaling 291. The 11 tactics are:

1. Initial access
2. Execution
3. Persistence
4. Privilege escalation
5. Defense evasion
6. Credential access
7. Discovery
8. Lateral movement
9. Collection
10. Exfiltration
11. Impact

To leverage the MITRE framework, developers and security professionals find the relevant technology, the tactic for evaluation, and then review which of the 291 techniques attackers could utilize to perform that movement against that piece of software or system. For example, if a security team wants to bolster defenses against attackers pivoting (lateral movement) from a Windows-based web server to another internal device, a threat analyst could look under the “Lateral Movement” section, finding web servers and review the listed techniques against the current security resources in place.

The key value of MITRE ATT\&CK framework is its comprehensiveness, relevance (it is updated frequently) and specificity. MITRE's ATT\&CK Navigator allows users to view a visualization of the 291 techniques overlaid against the 11 tactics.

**PASTA**

The Process for Attack Simulation and Threat Analysis (PASTA) is a risk-centric threat modeling framework that was first introduced in 2012. The PASTA model includes seven stages, each with its own respective activities, and outputs that are aligned with business objectives, compliance standards and technical requirements, making it a model that is more strategic than tactical.

The process starts with organizations defining their assets. Then, each asset is walked through the seven-step process, incorporating feedback from operations, management, technology, and development stakeholders. As the PASTA threat model incorporates business and impact analysis components, key organizational decision-makers and staff from outside of the IT department are involved in the process. At the end of the process, a summary of threat options, severity scores, and potential remediations are produced for each asset.

![](<../.gitbook/assets/3 (1)>)

The PASTA framework allows organizations to align their threat modeling process with their business objectives, compliance standards, and technical requirements. It also engages key decision-makers and staff from outside of IT department, which ensures that the risk management strategy is comprehensive, and aligns with the organization's specific needs.

**Persona non Grata**

Persona non Grata (PnG) is a creative threat modeling approach that utilizes an imaginary dangerous persona to perform malicious and unwanted behavior against a system or piece of software. The goal of PnG is to identify potential threats and vulnerabilities by simulating an attack from a malicious actor.

When using PnG, organizations first define the appropriate or typical use case that an asset is to be used. For each step of the process, they document the security measures in place. Finally, an alternative and malicious method or use case is identified that can be used to exploit it.

PnG is a unique approach to threat modeling as it allows organizations to identify vulnerabilities and potential threats by simulating an attack from a malicious actor. By defining the typical use case of an asset, and then identifying alternative and malicious methods, it helps organizations to strengthen their security measures and prevent potential attacks.

![](../.gitbook/assets/4)

### Bringing it all together <a href="#_qm5i3ak9vpp8" id="_qm5i3ak9vpp8"></a>

### ([What is threat modeling? - Infosec Resources](https://resources.infosecinstitute.com/topic/what-is-threat-modeling/)) <a href="#_n0yntyr3x8s8" id="_n0yntyr3x8s8"></a>

Ultimately, all threat model methodologies can help security professionals identify potential threats to their systems and operations. It is important for organizations to understand the depth, type, and scope of each, so the desired outputs and outcomes match their organization's needs.

Additionally, organizations should understand the importance of making threat modeling a regular part of their operational activity. This includes incorporating it into the system development life cycle, integrating its use in governance models, and regularly performing threat modeling at least each time new systems are to be introduced or there are significant changes to business operations as a result of internal or external forces.

By regularly performing threat modeling as a part of their operational activity, organizations can proactively identify and address potential vulnerabilities and threats, and improve their overall cybersecurity posture. As the threat landscape continues to evolve, it is crucial for organizations to stay informed and adapt their approach to threat modeling accordingly.
