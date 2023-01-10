# Threat Modeling

### **Threat Modeling** <a href="#_q6d96uvc57u8" id="_q6d96uvc57u8"></a>

### Introduction <a href="#_19r0n5nq3khu" id="_19r0n5nq3khu"></a>

Everything that touches the internet or enterprise systems faces constant cyber threat from internal and external sources, malicious or mistaken. And as technology evolves and our world becomes even more connected, the number of threats seems to grow at an even faster pace. In fact, the number of individually detected pieces of malware targeting software vulnerabilities grew at 151 percent in the third quarter of 2018 alone, resulting in what experts estimate will reach over $6 trillion in annual damage by 2021.

While organizations have a lot of tools and resources available to them to help combat cyber threats, one of the most important methods is threat modeling. Security professionals and software developers use this method to identify, evaluate and mitigate risks.

At a high level, threat modeling includes:

* Capturing the scope and scale of the system to be evaluated
* Profiling the potential attackers and the methods, tools and motivations that each have
* Documenting potential threats and potential mitigations to them

While threat modeling is recommended to be performed early in the development phase of software or system design so potential issues can be addressed early, threat modeling can also be an ongoing process that organizations undertake to evaluate risk overtime as conditions change.

Because of the role that threat modeling plays in establishing a strong cybersecurity posture in an organization, Infosec will be exploring all of the various facets of the practice in an upcoming series. However, before diving deeper into more advanced topics, it is important to begin with establishing a baseline understanding of threat modeling and how the practice has evolved over time.

### Threat modeling overview <a href="#_uc2w7omlecru" id="_uc2w7omlecru"></a>

Although there are various methods to facilitate threat modeling, all models seek to walk organizations through a structured process to identify the full range of potential security threats and vulnerabilities in a system or piece of software, evaluate the potential severity if exploited and prioritize them for mitigation.

To accomplish this, organizations must ask their security teams, engineers and developers to completely change their perspective from creating, securing and protecting to one where they are asked to envision potential attacks, exploit vulnerabilities and evaluate their own ability to defend against them with built in or proactive measures.

While it can be easy to bypass this step in the development life cycle or in the busyness of operations, it is important to remember the role that threat modeling plays. In a time when cyberattacks are widely published, concerns about customer data privacy are prominent and vulnerabilities are easily traded on the dark web, threat modeling helps your organization to approach cybersecurity in a structured and systematic way, with a shared understanding of the problem and a clear method to develop solutions.

Instead of performing stock system and user testing or finding a one-size-fits-all compliance or penetration testing checklist, threat modeling provides a deeper understanding of a system so that potential issues can be caught early, fixed and prevented before more costly remediation or incident response activities are required.

### The threat modeling process <a href="#_lkxcii45w1up" id="_lkxcii45w1up"></a>

As every organization, system and security team is unique, there are a variety of threat modeling methodologies that can be employed to meet their particular needs and goals. While each has their own slightly different naming convention and series of steps, the most prevalent threat models processes encompass roughly the same logical flow at their core.

As summarized by Carnegie Mellon University’s Software Engineering Institute, all threat models include:

*
  1. An abstraction of the system
  2. Profiles of potential attackers, including their goals and methods
  3. A catalog of potential threats that may arise

### Main threat modeling frameworks <a href="#_3ymj79xofkxa" id="_3ymj79xofkxa"></a>

While a complete breakdown of each of the main threat modeling frameworks is not within the scope of this article, the models introduced below represent ten of the most prevalent. As with other types of risk modeling, quantitative and qualitative analysis combine to demonstrate that threat modeling is still in many ways an art as opposed to a pure scientific process.

**Attack Trees**

No discussion about threat modeling can go without speaking to attack trees, which were first utilized as a method to document and address cyber risk by Bruce Schneier in the late 1990s. As with any logic model, an attack tree provides organizations with a visual, methodological method to describe systems and evaluate the different facets that make up its attack surface.

![](<../.gitbook/assets/0 (2)>)

As seen in the simple example above, the model begins with the root node representing the goal of the specific attack model or a particular component of a complex enterprise system. The next layer is a potential attack vector, followed by the different techniques or individual methods needed to perform each respective attack vector.

In short, the following six steps are used:

1. Identify assets
2. Identify threats
3. Understand threats
4. Categorize threats
5. Rate threats
6. Identify mitigation strategies or defensive measures

The resulting tree can be used to assist in making decisions, identifying vulnerable systems and evaluating the likelihood of certain attack vectors.

**STRIDE**

The cyber threat modeling method with the longest history, the STRIDE model was developed in 1999 by Microsoft employees Loren Kohnfleder and Praerit Garg. STRIDE directly links to the CIA triad and is an acronym that represents:

![](../.gitbook/assets/1)

The STRIDE threat modeling methodology aligns with Microsoft’s default security and privacy initiative, Trustworthy Computing, and is designed to give software developers the tools needed to integrate security directly into the software design phase.

The process begins with security professionals creating a data flow diagram that identifies the system’s components, events, interactions and boundaries. The diagram is then overlaid with a general set of known threats using the threat types identified above. As deviations or issues are identified in the system when compared to the STRIDE model, developers can then refine the target system. This process will continue until threats are either addressed or an organization reaches its defined level of acceptable risk.

**OCTAVE**

Developed by Carnegie Mellon University’s Software Engineering Institute (SEI) and CERT in 2003, the OCTAVE threat modeling methodology utilizes an enterprise-level perspective of cyber risk, focusing on organization-level risk — such as the impact of breaches of proprietary or customer data — instead of only assessing technology threats. OCTAVE is an acronym of Operationally Critical Threat, Asset and Vulnerability Evaluation.

Using the OCTAVE model, organizations move through three phases. First, all of the assets involved in storing, processing and transferring information across the organization as well as the associated datasets are captured, and attributes are assigned based on the type and sensitivity of the data. Next, the specific technical components and their associated vulnerabilities are documented. Finally, the information from Phase 1 and Phase 2 are evaluated, a security strategy and required resources are developed and identified and decisions to address or take action on them can be made by organizational leadership.

![](../.gitbook/assets/2)

**MITRE**

The MITRE Adversary Tactics Techniques and Common Knowledge (ATT\&CK) framework was launched in 2015 and, in a very short time, has become a well-known method for identifying, cataloging and understanding organizational vulnerabilities and cyberattack methods. The ATT\&CK framework is divided into 11 tactics, each further populated with a range of techniques that attackers could use, totaling 291.

The 11 tactics are:

* Initial access
* Execution
* Persistence
* Privilege escalation
* Defense evasion
* Credential access
* Discovery
* Lateral movement
* Collection
* Exfiltration
* Impact

Note: To see a visualization of the 291 techniques overlaid against the 11 tactics, you can view MITRE’s ATT\&CK Navigator.

To leverage the MITRE framework, developers and security professionals find the relevant technology, the tactic for evaluation, and then review which of the 291 techniques attackers could utilize to perform that movement against that piece of software or system. For example, if a security team wanted to bolster defenses against attackers pivoting (lateral movement) from a Windows-based web server to another internal device, a threat analyst could look under the “Lateral Movement” section, finding web servers and review the listed techniques against the current security resources in place.

While the “product” MITRE ATT\&CK framework is different from many other threat models, its value is in its comprehensiveness, its relevance (it is updated frequently) and in its specificity.

**PASTA**

The Process for Attack Simulation and Threat Analysis (PASTA) is a risk-centric threat modeling framework first introduced in 2012. The PASTA threat model includes seven stages, each with their own respective activities, with outputs that are aligned with business objectives, compliance standards and technical requirements, which makes it a model that is more strategic than it is tactical.

![](../.gitbook/assets/3)

To begin, organizations define their assets. Then each asset is walked through the seven-step process, incorporating feedback from operations, management, technology and development stakeholders. As the PASTA threat model incorporates business and impact analysis components, key organizational decision makers and staff from outside of the IT department are involved in the process. At the end of the process, a summary of threat options, severity scores and potential remediations are produced for each asset.

**Persona non Grata**

Persona non Grata (PnG) is another creative model that utilizes an imaginary dangerous persona to perform malicious, unwanted behavior against a system or to a piece of software. When using PnG, organizations first define the appropriate or typical use case that an asset is to be used and, for each step of the process, document the security measure in place. Finally, an alternative and malicious method or use case is identified that can be used to exploit it.

![](../.gitbook/assets/4)

### Bringing it all together <a href="#_qm5i3ak9vpp8" id="_qm5i3ak9vpp8"></a>

### ([What is threat modeling? - Infosec Resources](https://resources.infosecinstitute.com/topic/what-is-threat-modeling/)) <a href="#_n0yntyr3x8s8" id="_n0yntyr3x8s8"></a>

Ultimately, all threat model methodologies are able to help security professionals identify potential threats to their systems and their operations. Therefore, it is equally important for organizations to understand the depth, type and scope of each, so the desired outputs and outcomes match their organization’s needs.

Additionally, organizations need to understand the importance of making threat modeling a regular part of their operational activity, including it in their system development life cycle, integrating their use in governance models and regularly performing threat modeling at least each time new systems are to be introduced or there are significant changes to business operations as a result of internal or external forces.

As our Infosec series on threat modeling continues, we will explore more facets of the practice so you and your organization can make the best choice for your proactive cybersecurity purposes.
