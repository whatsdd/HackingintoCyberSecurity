# Information Security

### **Information Security** <a href="#_afb8c5557q51" id="_afb8c5557q51"></a>

**(**[Amazon.com: Principles of Information Security (MindTap Course List): 9780357506431](https://www.amazon.com/Principles-Information-Security-Mindtap-Course/dp/035750643X/ref=sr\_1\_1?keywords=information+security\&qid=1649738335\&s=books\&sprefix=information+sec%2Cstripbooks-intl-ship%2C578\&sr=1-1\&asin=B08QRLB2MQ\&revisionId=\&format=4\&depth=1) **)**

### Introduction to Infosec. <a href="#_qy8s4bnt2nv5" id="_qy8s4bnt2nv5"></a>

Martin Fisher, IT Security Manager at Northside Hospital in Atlanta, believes that enterprise information security is a “critical business capability that needs to be aligned with corporate expectations and culture that provides the leadership and insight to identify risks and implement effective controls.” He is not alone in his perspective. Many information security practitioners recognize that aligning information security needs with business objectives must be the top priority.

This chapter’s opening scenario illustrates that information risks and controls may not be in balance at SLS. Though Amy works in a technical support role to help users with their problems, she did not recall her training about malicious email attachments, such as worms or viruses, and fell victim to this form of attack herself. Understanding how malware might be the cause of a company’s problems is an important skill for information technology (IT) support staff as well as users. SLS’s management also shows signs of confusion and seems to have no idea how to contain this kind of incident. If you were in Amy’s place and were faced with a similar situation, what would you do? How would you react? Would it occur to you that something far more insidious than a technical malfunction was happening at your company? As you explore the chapters of this book and learn more about information security, you will become more capable of answering these questions. But, before you can begin studying details about the discipline of information security, you must first know its history and evolution.

**The History of Information Security**

The history of information security begins with the concept of computer security. The need for computer security arose during World War II when the first mainframe computers were developed and used to aid computations for communication code breaking messages from enemy cryptographic devices like the Enigma, shown in Figure 1-1. Multiple levels of security were implemented to protect these devices and the missions they served. This required new processes as well as tried-and-true methods needed to maintain data confidentiality. Access to sensitive military locations, for example, was controlled by means of badges, keys, and the facial recognition of authorized personnel by security guards. The growing need to maintain national security eventually led to more complex and technologically sophisticated computer security safeguards.

During these early years, information security was a straightforward process composed predominantly of physical security and simple document classification schemes. The primary threats to security were physical theft of equipment, espionage against products of the systems, and sabotage. One of the first documented security problems that fell outside these categories occurred in the early 1960s, when a systems administrator was working on a MOTD (message of the day) file while another administrator was editing the password file. A software glitch mixed the two files, and the entire password file was printed on every output file.

**What Is Security?**

Security is protection. Protection from adversaries—those who would do harm, intentionally or otherwise—is the ultimate objective of security. National security, for example, is a multilayered system that protects the sovereignty of a state, its assets, its resources, and its people. Achieving the appropriate level of security for an organization also requires a multifaceted system. A successful organization should have multiple layers of security in place to protect its operations, physical infrastructure, people, functions, communications, and information.

The Committee on National Security Systems (CNSS) defines information security as the protection of information and its critical elements, including the systems and hardware that use, store, and transmit the information. Information security includes the broad areas of information security management, data security, and network security. The CNSS model of information security evolved from a concept developed by the computer security industry called the C.I.A. triad. The C.I.A. triad has been the standard for computer security in both industry and government since the development of the mainframe. This standard is based on the three characteristics of information that give it value to organizations: confidentiality, integrity, and availability. The security of these three characteristics is as important today as it has always been, but the C.I.A. triad model is generally viewed as no longer adequate in addressing the constantly changing environment. The threats to the confidentiality, integrity, and availability of information have evolved into a vast collection of events, including accidental or intentional damage, destruction, theft, unintended or unauthorized modification, or other misuse from human or nonhuman threats. This vast array of constantly evolving threats has prompted the development of a more robust model that addresses the complexities of the current information security environment. The expanded model consists of a list of critical characteristics of information, which are described in the next section. C.I.A. triad terminology is used in this chapter because of the breadth of material that is based on it.

**Key Information Security Concepts**

This book uses many terms and concepts that are essential to any discussion of information security. Some of these terms are illustrated in Figure 1-7; all are covered in greater detail in subsequent chapters.

* **Access:** A subject or object’s ability to use, manipulate, modify, or affect another subject or object. Authorized users have legal access to a system, whereas hackers must gain illegal access to a system. Access controls regulate this ability.
* **Asset:** The organizational resource that is being protected. An asset can be logical, such as a Web site, software information, or data; or an asset can be physical, such as a person, computer system, hardware, or other tangible object. Assets, particularly information assets, are the focus of what security efforts are attempting to protect.
* **Attack:** An intentional or unintentional act that can damage or otherwise compromise information and the systems that support it. Attacks can be active or passive, intentional or unintentional, and direct or indirect. Someone who casually reads sensitive information not intended for his or her use is committing a passive attack. A hacker attempting to break into an information system is an intentional attack. A lightning strike that causes a building fire is an unintentional attack. A direct attack is perpetrated by a hacker using a PC to break into a system. An indirect attack is a hacker compromising a system and using it to attack other systems—for example, as part of a botnet (slang for robot network). This group of compromised computers, running software of the attacker’s choosing, can operate autonomously or under the attacker’s direct control to attack systems and steal user information or conduct distributed denial-of-service attacks. Direct attacks originate from the threat itself. Indirect attacks originate from a compromised system or resource that is malfunctioning or working under the control of a threat.
* **Control, safeguard, or countermeasure:** Security mechanisms, policies, or procedures that can successfully counter attacks, reduce risk, resolve vulnerabilities, and otherwise improve security within an organization. The various levels and types of controls are discussed more fully in the following chapters.
* **Exploit**: A technique used to compromise a system. This term can be a verb or a noun. Threat agents may attempt to exploit a system or other information asset by using it illegally for their personal gain. Or, an exploit can be a documented process to take advantage of a vulnerability or exposure, usually in software, that is either inherent in the software or created by the attacker. Exploits make use of existing software tools or custom-made software components.
* **Exposure:** A condition or state of being exposed; in information security, exposure exists when a vulnerability is known to an attacker.
* **Loss:** A single instance of an information asset suffering damage or destruction, unintended or unauthorized modification or disclosure, or denial of use. When an organization’s information is stolen, it has suffered a loss.
* **Protection profile or security posture:** The entire set of controls and safeguards, including policy, education, training and awareness, and technology, that the organization implements to protect the asset. The terms are sometimes used interchangeably with the term security program, although a security program often comprises managerial aspects of security, including planning, personnel, and subordinate programs.
* **Risk:** The probability of an unwanted occurrence, such as an adverse event or loss. Organizations must minimize risk to match their risk appetite—the quantity and nature of risk they are willing to accept.
* **Subjects and objects of attack:** A computer can be either the subject of an attack—an agent entity used to conduct the attack—or the object of an attack: the target entity, as shown in Figure 1-8. A computer can also be both the subject and object of an attack. For example, it can be compromised by an attack (object) and then used to attack other systems (subject).
* **Threat:** Any event or circumstance that has the potential to adversely affect operations and assets. The term threat source is commonly used interchangeably with the more generic term threat. While the two terms are technically distinct, in order to simplify discussion, the text will continue to use the term threat to describe threat sources.
* **Threat agent:** The specific instance or a component of a threat. For example, the threat source of “trespass or espionage” is a category of potential danger to information assets, while “external professional hacker” (like Kevin Mitnick, who was convicted of hacking into phone systems) is a specific threat agent. A lightning strike, hailstorm, or tornado is a threat agent that is part of the threat source known as “acts of God/acts of nature.”
* **Threat event:** An occurrence of an event caused by a threat agent. An example of a threat event might be damage caused by a storm. This term is commonly used interchangeably with the term attack.

### The Need for Security <a href="#_t9b6gygaxese" id="_t9b6gygaxese"></a>

Unlike any other business or information technology program, the primary mission of an information security program is to ensure that information assets—information and the systems that house them—remain safe and useful. Organizations expend a lot of money and thousands of hours to maintain their information assets. If threats to these assets didn’t exist, those resources could be used exclusively to improve the systems that contain, use, and transmit the information. However, the threat of attacks on information assets is a constant concern, and the need for information security grows along with the sophistication of the attacks. While some organizations lump both information and systems under their definition of an information asset, others prefer to separate the true information-based assets (data, databases, data sets, and the applications that may use data) from media—the systems and networks that store and transmit data. For our purposes, we will include both data and systems assets in our use of the term.

Organizations must understand the environment in which information assets reside so their information security programs can address actual and potential problems. This chapter describes the environment and identifies the threats to it, the organization, and its information.

Information security performs four important functions for an organization:

* Protecting the organization’s ability to function
* Protecting the data and information the organization collects and uses, whether physical or electronic
* Enabling the safe operation of applications running on the organization’s IT systems
* Safeguarding the organization’s technology assets

**Protecting Functionality**

The three communities of interest—general management, IT management, and information security management—are each responsible for facilitating the information security program that protects the organization’s ability to function. Although many business and government managers shy away from addressing information security because they perceive it to be a technically complex task, implementing information security actually has more to do with management than technology. Just as managing payroll involves management more than mathematical wage computations, managing information security has more to do with risk management, policy, and its enforcement than the technology of its implementation. As the noted information security author Charles Cresson Wood writes:

_In fact, a lot of \[information security] is good management for information technology. Many people think that a solution to a technology problem is more technology. Well, not necessarily.… So a lot of my work, out of necessity, has been trying to get my clients to pay more attention to information security as a management issue in addition to a technical issue, information security as a people issue in addition to the technical issue._

Each of an organization’s communities of interest must address information security in terms of business impact and the cost of business interruption, rather than isolating security as a technical problem.

**Protecting Data That Organizations Collect and Use**

Without data, an organization loses its record of transactions and its ability to deliver value to customers. Any business, educational institution, or government agency that operates within the modern context of connected and responsive services relies on information systems. Even when transactions are not online, information systems and the data they process enable the creation and movement of goods and services. Therefore, data security—protecting data in transmission, in processing, and at rest (storage)—is a critical aspect of information security. The value of data motivates attackers to steal, sabotage, or corrupt it. An effective information security program implemented by management protects the integrity and value of the organization’s data.

Organizations store much of the data they deem critical in databases, managed by specialized data management software known as a database management system (DBMS). The process of maintaining the confidentiality, integrity, and availability of data managed by a DBMS is known as database security. Database security is accomplished by applying a broad range of control approaches common to many areas of information security. Securing databases encompasses most of the topics you will cover in this textbook, including managerial, technical, and physical controls. Managerial controls include policy, procedure, and governance. Technical controls used to secure databases rely on knowledge of access control, authentication, auditing, application security, backup and recovery, encryption, and integrity controls. Physical controls include the use of data centers with locking doors, fire suppression systems, video monitoring, and physical security guards.

The fundamental practices of information security have broad applicability in the area of database security. One indicator of this strong degree of overlap is that the International Information Systems Security Certification Consortium (ISC)2 , the organization that evaluates candidates for many prestigious information security certification programs, allows experience as a database administrator to count toward the experience requirement for the Certified Information Systems Security Professional (CISSP).

**Enabling the Safe Operation of Applications**

Today’s organizations are under immense pressure to acquire and operate integrated, efficient, and capable applications. A modern organization needs to create an environment that safeguards these applications, particularly those that are important elements of the organization’s infrastructure— operating system platforms, certain operational applications, electronic mail (e-mail), and instant messaging (IM) applications, like text messaging (short message service, or SMS). Organizations acquire these elements from a service provider or they implement their own. Once an organization’s infrastructure is in place, management must continue to oversee it and not relegate its management to the IT department.

**Safeguarding Technology Assets in Organizations**

To perform effectively, organizations must employ secure infrastructure hardware appropriate to the size and scope of the enterprise. For instance, a small business may get by in its startup phase using a small-scale firewall, such as a small office/home office (SOHO) device.

In general, as an organization grows to accommodate changing needs, more robust technology solutions should replace security technologies the organization has outgrown. An example of a robust solution is a commercial-grade, unified security architecture device complete with intrusion detection and prevention systems, public key infrastructure (PKI), and virtual private network (VPN) capabilities. Chapters 6 through 8 describe these technologies in more detail.

Information technology continues to add new capabilities and methods that allow organizations to solve business information management challenges. In recent years we have seen the emergence of the Internet and the Web as new markets. Cloud-based services, which have created new ways to deliver IT services, have also brought new risks to organizational information, additional concerns about the ways these assets can be threatened, and concern for how they must be defended.

**Compromises to Intellectual Property**

Many organizations create or support the development of intellectual property (IP) as part of their business operations. (You will learn more about IP in Chapter 3.) IP includes trade secrets, copyrights, trademarks, and patents. IP is protected by copyright law and other laws, carries the expectation of proper attribution or credit to its source, and potentially requires the acquisition of permission for its use, as specified in those laws. For example, use of some IP may require specific payments or royalties before a song can be used in a movie or before the distribution of a photo in a publication. The unauthorized appropriation of IP constitutes a threat to information security. Employees may have access privileges to a variety of IP, including purchased and developed software and organizational information, as many employees typically need to use IP to conduct day-to-day business.

Organizations often purchase or lease the IP of other organizations, and must abide by a purchase or licensing agreement for its fair and responsible use. The most common IP breach is the unlawful use or duplication of software-based intellectual property, more commonly known as software piracy. Because most software is licensed to a particular purchaser, its use is restricted to a single user or to a designated user in an organization. If a user copies the program to another computer without securing another license or transferring the license, the user has violated the copyright. The nearby Offline feature describes a classic case of this type of copyright violation. While you may note that the example is from 1997, which seems a long time ago, it illustrates that the issue remains significant today.

Software licenses are strictly enforced by regulatory and private organizations, and software publishers use several control mechanisms to prevent copyright infringement. In addition to laws against software piracy, two watchdog organizations investigate allegations of software abuse: the Software & Information Industry Association (SIIA) at www.siia.net, formerly known as the Software Publishers Association, and the Business Software Alliance (BSA) at www.bsa.org. BSA estimates that approximately 39 percent of software installed on computers globally in 2015 was not properly licensed. This number is only slightly lower than the 43 percent reported in the 2013 BSA global study. Furthermore, about 26 percent of employees who responded to the 2015 study admitted installing unauthorized software on computers at work; over 84 percent of those employees installed two or more software packages. BSA also reports a modest global decline in the use of unlicensed software—down 4 percent from 2013 to an estimated commercial value of $52.2 billion.8 Figure 2-2 shows the BSA’s software piracy reporting Web site.

**Deviations in Quality of Service**

An organization’s information system depends on the successful operation of many interdependent support systems, including power grids, data and telecommunications networks, parts suppliers, service vendors, and even janitorial staff and garbage haulers. Any of these support systems can be interrupted by severe weather, employee illnesses, or other unforeseen events. Deviations in quality of service can result from such accidents as a backhoe taking out an ISP’s fiber-optic link. The backup provider may be online and in service, but may be able to supply only a fraction of the bandwidth the organization needs for full service. This degradation of service is a form of availability disruption. Irregularities in Internet service, communications, and power supplies can dramatically affect the availability of information and systems.

* **Internet Service Issues**

In organizations that rely heavily on the Internet and the World Wide Web to support continued operations, ISP failures can considerably undermine the availability of information. Many organizations have sales staff and telecommuters working at remote locations. When these off-site employees cannot contact the host systems, they must use manual procedures to continue operations. The U.S. government’s Federal Communications Commission (FCC) maintains a Network Outage Reporting System (NORS), which according to FCC regulation 47 C.F.R. Part 4, requires communications providers to report outages that disrupt communications at certain facilities, like emergency services and airports.

When an organization places its Web servers in the care of a Web hosting provider, that provider assumes responsibility for all Internet services and for the hardware and operating system software used to operate the Web site. These Web hosting services are usually arranged with a service level agreement (SLA). When a service provider fails to meet the terms of the SLA, the provider may accrue fines to cover losses incurred by the client, but these payments seldom cover the losses generated by the outage. Vendors may promote high availability or uptime (or low downtime), but Figure 2-5 shows even an availability that seems acceptably high can cost the average organization a great deal. In August 2013, the Amazon.com Web site went down for 30 to 40 minutes, costing the company between $3 million and $4 million.

* **Communications and Other Service Provider Issues**

Other utility services can affect organizations as well. Among these are telephone, water, wastewater, trash pickup, cable television, natural or propane gas, and custodial services. The loss of these services can impair the ability of an organization to function. For instance, most facilities require water service to operate an air-conditioning system. Even in Minnesota in February, air-conditioning systems help keep a modern facility operating. If a wastewater system fails, an organization might be prevented from allowing employees into the building. While several online utilities allow an organization to compare pricing options from various service providers, only a few show a comparative analysis of availability or downtime.

* **Power Irregularities**

Irregularities from power utilities are common and can lead to fluctuations such as power excesses, power shortages, and power losses. These fluctuations can pose problems for organizations that provide inadequately conditioned power for their information systems equipment. In the United States, we are supplied 120-volt, 60-cycle power, usually through 15- and 20-amp circuits. Europe as well as most of Africa, Asia, South America, and Australia use 230-volt, 50-cycle power. With the prevalence of global travel by organizational employees, failure to properly adapt to different voltage levels can damage computing equipment, resulting in a loss. When power voltage levels vary from normal, expected levels, such as during a spike, surge, sag, fault, noise, brownout, or blackout, an organization’s sensitive electronic equipment—especially networking equipment, computers, and computer based systems, which are vulnerable to fluctuations—can be easily damaged or destroyed. With small computers and network systems, quality power-conditioning options such as surge suppressors can smooth out spikes. The more expensive uninterruptible power supply (UPS) can protect against spikes and surges as well as sags and even blackouts of limited duration. UPSs are discussed in additional detail in Chapter 9, “Physical Security.”

**Espionage or Trespass**

Espionage or trespass is a well-known and broad category of electronic and human activities that can breach the confidentiality of information. When an unauthorized person gains access to information an organization is trying to protect, the act is categorized as espionage or trespass. Attackers can use many different methods to access the information stored in an information system. Some information-gathering techniques are legal—for example, using a Web browser to perform market research. These legal techniques are collectively called competitive intelligence. When information gatherers employ techniques that cross a legal or ethical threshold, they are conducting industrial espionage. Many countries that are considered allies of the United States engage in industrial espionage against American organizations. When foreign governments are involved, these activities are considered espionage and a threat to national security.

Some forms of espionage are relatively low tech. One example, called shoulder surfing, is pictured in Figure 2-6. This technique is used in public or semipublic settings when people gather information they are not authorized to have. Instances of shoulder surfing occur at computer terminals, desks, and ATMs; on a bus, airplane, or subway, where people use smartphones and tablet PCs; and in other places where employees may access confidential information.

Shoulder surfing flies in the face of the unwritten etiquette among professionals who address information security in the workplace: If you can see another person entering personal or private information into a system, look away as the information is entered. Failure to do so constitutes not only a breach of etiquette, but an affront to privacy and a threat to the security of confidential information.

Acts of trespass can lead to unauthorized real or virtual actions that enable information gatherers to enter premises or systems without permission. Controls sometimes mark the boundaries of an organization’s virtual territory. These boundaries give notice to trespassers that they are encroaching on the organization’s cyberspace. Sound principles of authentication and authorization can help organizations protect valuable information and systems. These control methods and technologies employ multiple layers or factors to protect against unauthorized access and trespass.

The classic perpetrator of espionage or trespass is the hacker, who is frequently glamorized in fictional accounts as a person who stealthily manipulates a maze of computer networks, systems, and data to find information that solves the mystery and heroically saves the day. However, the true life of the hacker is far more mundane. The profile of the typical hacker has shifted from that of a 13- to 18-year-old male with limited parental supervision who spends all of his free time on the computer to a person with fewer known attributes (see Figure 2-7). In the real world, a hacker frequently spends long hours examining the types and structures of targeted systems and uses skill, guile, or fraud to attempt to bypass controls placed on information owned by someone else.

### Legal, Ethical, and Professional Issues in Information Security <a href="#_2uqu16xkcqkj" id="_2uqu16xkcqkj"></a>

As a future information security professional, or an IT professional with security responsibilities, you must understand the scope of an organization’s legal and ethical responsibilities. The information security professional plays an important role in an organization’s approach to managing responsibility and liability for privacy and security risks. In modern litigious societies around the world, laws are sometimes enforced in civil courts, where large damages can be awarded to plaintiffs who bring suits against organizations. Sometimes these damages are punitive—a punishment assessed as a deterrent to future transgressions. To minimize liability and reduce risks from electronic and physical threats, and to reduce all losses from legal action, information security practitioners must thoroughly understand the current legal environment, stay current with laws and regulations, and watch for new and emerging issues. By educating the management and employees of an organization on their legal and ethical obligations and the proper use of information technology and information security, security professionals can help keep an organization focused on its primary business objectives.

In the first part of this chapter, you will learn about the legislation and regulations that affect the management of information in an organization. In the second part, you will learn about the ethical issues related to information security, and about several professional organizations with established codes of ethics. Use this chapter both as a reference to the legal aspects of information security and as an aid in planning your professional career.

In general, people elect to trade some aspects of personal freedom for social order. It is often a necessary but somewhat ironic proposition, as Benjamin Franklin asserted: “Those who would give up essential Liberty, to purchase a little temporary Safety, deserve neither Liberty nor Safety.”1 As Jean-Jacques Rousseau explained in The Social Contract, or Principles of Political Right, 2 the rules that members of a society create to balance the individual rights to self-determination against the needs of the society as a whole are called laws. The key difference between laws and ethics is that laws carry the authority of a governing body and ethics do not. Ethics in turn are based on cultural mores. Some ethical standards are universal. For example, murder, theft, assault, and arson are generally prohibited in ethical and legal codes throughout the world.

**Organizational Liability and the Need for Counsel**

What if an organization does not demand or even encourage strong ethical behavior from its employees? What if an organization does not behave ethically? Even if there is no breach of criminal law, there can still be liability—legal responsibility. Liability includes the legal obligation to make restitution for wrongs committed. The bottom line is that if an employee performs an illegal or unethical act that causes some degree of harm, the employer can be held financially liable for that action, regardless of whether the employer authorized the act. An organization increases its liability if it refuses to take measures known as due care (or a standard of due care). Similarly, due diligence requires that an organization make a valid attempt to continually maintain this level of effort. Whereas due care means the organization acts legally and ethically, due diligence means it ensures compliance with this level of expected behavior. Given the Internet’s global reach, those who could be injured or wronged by an organization’s employees might live anywhere in the world. Under the U.S. legal system, any court can assert its authority over an individual or organization if it can establish jurisdiction. This is sometimes referred to as long-arm jurisdiction when laws are stretched to apply to parties in distant locations. Trying a case in the injured party’s home area is usually favorable to the injured party.

**Policy Versus Law**

Within an organization, information security professionals help maintain security via the establishment and enforcement of policy. As discussed in greater detail in Chapter 4, “Planning for Security,” these policies function as organizational laws, complete with penalties, judicial practices, and sanctions to require compliance. Because these policies function as laws, they must be crafted and implemented with the same care to ensure that they are complete, appropriate, and fairly applied to everyone in the workplace. The difference between a policy and a law, however, is that ignorance of a policy is an acceptable defense. Policies must be able to stand up in court if challenged, because if an employee is fired based on a policy violation, rest assured it will be challenged. Thus, for a policy to be enforceable, it must meet the following five criteria:

* **Dissemination (distribution):** The organization must be able to demonstrate that the relevant policy has been made readily available for review by the employee. Common dissemination techniques include hard copy and electronic distribution.
* **Review (reading):** The organization must be able to demonstrate that it disseminated the document in an intelligible form, including versions for employees who are illiterate, reading-impaired, and unable to read English. Common techniques include recordings of the policy in English and alternate languages.
* **Comprehension (understanding):** The organization must be able to demonstrate that the employee understands the requirements and content of the policy. Common techniques include quizzes and other assessments.
* **Compliance (agreement):** The organization must be able to demonstrate that the employee agreed to comply with the policy through act or affirmation. Common techniques include logon banners, which require a specific action (mouse click or keystroke) to acknowledge agreement, or a signed document clearly indicating the employee has read, understood, and agreed to comply with the policy.
* **Uniform enforcement:** The organization must be able to demonstrate that the policy has been uniformly enforced, regardless of employee status or assignment.

Only when all of these conditions are met can an organization penalize employees who violate a policy without fear of legal retribution.

**Types of Law**

There are a number of ways to categorize laws within the United States. In addition to the hierarchical perspective of local, state, federal, and international laws, most U.S. laws can be categorized based on their origins:

* Constitutional Law: Originates with the U.S. Constitution, a state constitution, or local constitution, bylaws, or charter.
* Statutory Law: Originates from a legislative branch specifically tasked with the creation and publication of laws and statutes.
* Regulatory or Administrative Law: Originates from an executive branch or authorized regulatory agency, and includes executive orders and regulations.
* Common Law, Case Law, and Precedent: Originates from a judicial branch or oversight board and involves the interpretation of law based on the actions of a previous and/or higher court or board.

Within statutory law, one can further divide laws into their association with individuals, groups, and the “state”:

**Civil law** embodies a wide variety of laws pertaining to relationships between and among individuals and organizations. Civil law includes contract law, employment law, family law, and tort law. Tort law is the subset of civil law that allows individuals to seek redress in the event of personal, physical, or financial injury. Perceived damages within civil law are pursued in civil court and are not prosecuted by the state.

**Criminal law** addresses violations harmful to society and is actively enforced and prosecuted by the state. Criminal law addresses statutes associated with traffic law, public order, property damage, and personal damage, where the state takes on the responsibility of seeking retribution on behalf of the plaintiff, or injured party.

### Principles of Infosec. <a href="#_yvv76vmiq5dn" id="_yvv76vmiq5dn"></a>

The basic tenets of information security are confidentiality, integrity and availability. Every element of the information security program must be designed to implement one or more of these principles. Together they are called the CIA Triad.

* **Confidentiality**

Confidentiality measures are designed to prevent unauthorized disclosure of information. The purpose of the confidentiality principle is to keep personal information private and to ensure that it is visible and accessible only to those individuals who own it or need it to perform their organizational functions.

* **Integrity**

Consistency includes protection against unauthorized changes (additions, deletions, alterations, etc.) to data. The principle of integrity ensures that data is accurate and reliable and is not modified incorrectly, whether accidentally or maliciously.

* **Availability**

Availability is the protection of a system’s ability to make software systems and data fully available when a user needs it (or at a specified time). The purpose of availability is to make the technology infrastructure, the applications and the data available when they are needed for an organizational process or for an organization’s customers.

![](../.gitbook/assets/0)

### Information Security vs Cybersecurity <a href="#_yy9l0b9la2cm" id="_yy9l0b9la2cm"></a>

Information security differs from cybersecurity in both scope and purpose. The two terms are often used interchangeably, but more accurately, cybersecurity is a subcategory of information security. Information security is a broad field that covers many areas such as physical security, endpoint security, data encryption, and network security. It is also closely related to information assurance, which protects information from threats such as natural disasters and server failures.

Cybersecurity primarily addresses technology-related threats, with practices and tools that can prevent or mitigate them. Another related category is data security, which focuses on protecting an organization’s data from accidental or malicious exposure to unauthorized parties.

### Information Security Policy <a href="#_sci6nolxk8gb" id="_sci6nolxk8gb"></a>

An Information Security Policy (ISP) is a set of rules that guide individuals when using IT assets. Companies can create information security policies to ensure that employees and other users follow security protocols and procedures. Security policies are intended to ensure that only authorized users can access sensitive systems and information.

Creating an effective security policy and taking steps to ensure compliance is an important step towards preventing and mitigating security threats. To make your policy truly effective, update it frequently based on company changes, new threats, conclusions drawn from previous breaches, and changes to security systems and tools.

Make your information security strategy practical and reasonable. To meet the needs and urgency of different departments within the organization, it is necessary to deploy a system of exceptions, with an approval process, enabling departments or individuals to deviate from the rules in specific circumstances.

### Top Information Security Threats <a href="#_43ndwd4tq64t" id="_43ndwd4tq64t"></a>

There are hundreds of categories of information security threats and millions of known threat vectors. Below we cover some of the key threats that are a priority for security teams at modern enterprises.

**Unsecure or Poorly Secured Systems**

The speed and technological development often leads to compromises in security measures. In other cases, systems are developed without security in mind, and remain in operation at an organization as legacy systems. Organizations must identify these poorly secured systems, and mitigate the threat by securing or patching them, decommissioning them, or isolating them.

**Social Media Attacks**

Many people have social media accounts, where they often unintentionally share a lot of information about themselves. Attackers can launch attacks directly via social media, for example by spreading malware via social media messages, or indirectly, by using information obtained from these sites to analyze user and organizational vulnerabilities, and use them to design an attack.

**Social Engineering**

Social engineering involves attackers sending emails and messages that trick users into performing actions that may compromise their security or divulge private information. Attackers manipulate users using psychological triggers like curiosity, urgency or fear.

Because the source of a social engineering message appears to be trusted, people are more likely to comply, for example by clicking a link that installs malware on their device, or by providing personal information, credentials, or financial details.

Organizations can mitigate social engineering by making users aware of its dangers and training them to identify and avoid suspected social engineering messages. In addition, technological systems can be used to block social engineering at its source, or prevent users from performing dangerous actions such as clicking on unknown links or downloading unknown attachments.

**Malware on Endpoints**

Organizational users work with a large variety of endpoint devices, including desktop computers, laptops, tablets, and mobile phones, many of which are privately owned and not under the organization’s control, and all of which connect regularly to the Internet.

A primary threat on all these endpoints is malware, which can be transmitted by a variety of means, can result in compromise of the endpoint itself, and can also lead to privilege escalation to other organizational systems.

Traditional antivirus software is insufficient to block all modern forms of malware, and more advanced approaches are developing to securing endpoints, such as endpoint detection and response (EDR).

**Lack of Encryption**

Encryption processes encode data so that it can only be decoded by users with secret keys. It is very effective in preventing data loss or corruption in case of equipment loss or theft, or in case organizational systems are compromised by attackers.

Unfortunately, this measure is often overlooked due to its complexity and lack of legal obligations associated with proper implementation. Organizations are increasingly adopting encryption, by purchasing storage devices or using cloud services that support encryption, or using dedicated security tools.

**Security Misconfiguration**

Modern organizations use a huge number of technological platforms and tools, in particular web applications, databases, and Software as a Service (SaaS) applications, or Infrastructure as a Service (IaaS) from providers like Amazon Web Services.

Enterprise grade platforms and cloud services have security features, but these must be configured by the organization. Security misconfiguration due to negligence or human error can result in a security breach. Another problem is “configuration drift”, where correct security configuration can quickly become out of date and make a system vulnerable, unbeknownst to IT or security staff.

Organizations can mitigate security misconfiguration using technological platforms that continuously monitor systems, identify configuration gaps, and alert or even automatically remediate configuration issues that make systems vulnerable.

### Active vs Passive Attacks <a href="#_wohw6t6jzfm1" id="_wohw6t6jzfm1"></a>

Information security is intended to protect organizations against malicious attacks. There are two primary types of attacks: active and passive. Active attacks are considered more difficult to prevent, and the focus is on detecting, mitigating and recovering from them. Passive attacks are easier to prevent with strong security measures.

**Active Attack**

An active attack involves intercepting a communication or message and altering it for malicious effect. There are three common variants of an active attacks:

* Interruption—the attacker interrupts the original communication and creates new, malicious messages, pretending to be one of the communicating parties.
* Modification—the attacker uses existing communications, and either replays them to fool one of the communicating parties, or modifies them to gain an advantage.
* Fabrication—creates fake, or synthetic, communications, typically with the aim of achieving denial of service (DoS). This prevents users from accessing systems or performing normal operations.

**Passive Attack**

In a passive attack, an attacker monitors, monitors a system, and illicitly copies information without altering it. They then use this information to disrupt networks or compromise target systems.

The attackers do not make any changes to the communication or the target systems. This makes it more difficult to detect. However, encryption can help prevent passive attacks because it obfuscates the data, making it more difficult for attackers to make use of it.

### Information Security and Data Protection Laws <a href="#_6ii6mx79hnq" id="_6ii6mx79hnq"></a>

Information security is in constant interaction with the laws and regulations of the places where an organization does business. Data protection regulations around the world focus on enhancing the privacy of personal data, and place restrictions on the way organizations can collect, store, and make use of customer data.

Data privacy focuses on personally identifiable information (PII) and is primarily concerned with how the data is stored and used. PII includes any data that can be linked directly to the user, such as name, ID number, date of birth, physical address, or phone number. It may also include artifacts like social media posts, profile pictures, and IP addresses.

**Data Protection Laws in the European Union (EU): the GDPR**

The most known privacy law in the EU is the General Data Protection Regulation (GDPR). This regulation covers the collection, use, storage, security, and transmission of data related to EU residents.

The GDPR applies to any organization doing business with EU citizens, regardless of whether the company itself is based inside or outside the European Union. Violation of the guidelines may result in fines of up to 4% of global sales or 20 million Euro.

The main goals of the GDPR are:

* Setting the privacy of personal data as a basic human right
* Implementing privacy criteria requirements
* Standardization of how privacy rules are applied

GDPR includes protection of the following data types:

* Personal information such as name, ID number, date of birth, or address
* Web data such as IP address, cookies, location, etc.
* Health information including diagnosis and prognosis
* Biometric data including voice data, DNA, and fingerprints
* Private communications
* Photos and videos
* Cultural, social or economic data
