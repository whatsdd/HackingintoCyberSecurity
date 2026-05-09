# Introduction to Cyber Security

## What Cybersecurity Actually Is

Cybersecurity is the practice of protecting systems, networks, and data from unauthorized access, damage, or attack. That definition is accurate but undersells the scope. Modern cybersecurity covers everything from a teenager's laptop to hospital systems to power grids. The field exists because everything of value now lives in or passes through digital infrastructure, and digital infrastructure has vulnerabilities.

The term "cyberspace" was coined by William Gibson in his 1982 short story "Burning Chrome" and expanded in his 1984 novel *Neuromancer*, where he described it as "a consensual hallucination experienced daily by billions of legitimate operators."[1] The word caught on. What Gibson imagined as science fiction became, roughly, the internet. The word stuck, and with it came the field dedicated to securing that space.

Technically, cybersecurity is a subset of information security that specifically addresses electronic systems and the threats that target them. In practice the two terms are often used interchangeably, but the distinction matters: a locked filing cabinet is an information security control, not a cybersecurity control. The field encompasses the people, processes, and technologies that protect digital systems, and all three matter equally.[2]

---

## The Threat Landscape

The motivation behind most cyberattacks falls into four categories: financial gain, espionage, disruption, and reputation damage. Nation-state actors, organized criminal groups, insider threats, and amateur hackers all operate in this space, and they are not equally dangerous.

The most common threat to most organizations is financially motivated crime. Ransomware, business email compromise, and payment card fraud account for the majority of incidents that security teams deal with on a daily basis. The Verizon Data Breach Investigations Report, which analyzes tens of thousands of incidents annually, consistently shows that organized criminal groups and financially motivated actors are responsible for most confirmed breaches.[3]

Nation-state actors are the most sophisticated and the most patient. They operate on timelines measured in months or years, and their goal is often intelligence gathering rather than immediate financial return. The 2020 SolarWinds supply chain compromise, attributed to Russian intelligence services, is one of the clearest examples of how deeply a patient adversary can embed itself before being discovered. The attackers had access to roughly 18,000 organizations for months before detection.[4]

Understanding who is attacking matters. A startup facing financial fraud needs a different defense than a defense contractor facing state-sponsored espionage.

---

## Common Attack Types

Understanding how attacks work is foundational to defending against them, regardless of which career path you pursue.

**Phishing** is the most common initial access technique. An attacker sends a message designed to appear trustworthy, with the goal of tricking the recipient into clicking a link, opening an attachment, or providing credentials. Spear phishing targets specific individuals using personalized information. Whaling targets executives. Business email compromise (BEC) spoofs or compromises email accounts to authorize fraudulent wire transfers. The FBI's Internet Crime Complaint Center reported $2.7 billion in losses attributed to BEC in 2022 alone.[5]

**Denial of Service (DoS) and Distributed Denial of Service (DDoS)** attacks overwhelm a system or network with traffic, making it unavailable to legitimate users. DDoS attacks use botnets — networks of compromised machines — to amplify the volume of traffic. The 2016 Mirai botnet attack leveraged compromised IoT devices to knock large portions of the internet offline, affecting Twitter, Reddit, and Netflix.[6]

**Man-in-the-Middle (MitM)** attacks intercept communication between two parties. The attacker positions themselves between the sender and receiver, potentially reading, modifying, or injecting messages without either party knowing. Encryption is the primary defense.

**SQL Injection** exploits poorly validated input fields in web applications to insert malicious database commands. A successful SQL injection can expose entire databases, modify records, or grant an attacker administrative access. It has appeared on the OWASP Top 10 list of critical web application vulnerabilities for over a decade.[7]

**Cross-Site Scripting (XSS)** injects malicious scripts into web pages viewed by other users. The scripts run in the victim's browser, enabling session hijacking, credential theft, and malware delivery.

**Brute Force and Credential Attacks** systematically attempt every possible password combination, or use lists of previously breached credentials in credential stuffing attacks. With over 15 billion stolen credentials available on dark web markets, credential-based attacks remain persistently effective.[8]

**Social Engineering** manipulates people rather than exploiting technical vulnerabilities. Pretexting, vishing (voice phishing), and physical tailgating all fall under this category. Technical controls cannot stop an attack that convinces a legitimate user to voluntarily take a harmful action.

---

## Malware: A Field Guide

Malware is software designed to damage, disrupt, or gain unauthorized access to systems. The major types:

**Viruses** attach to legitimate files and replicate when those files are executed. They require a host file and human action to spread.

**Worms** replicate and spread across networks without needing a host file or human intervention. They can propagate at machine speed, which is why a worm like WannaCry infected over 200,000 systems across 150 countries in a single day in 2017.[9]

**Trojans** disguise themselves as legitimate software. Unlike viruses and worms, they do not self-replicate but rely on the user to install them.

**Ransomware** encrypts the victim's data and demands payment for the decryption key. Modern ransomware groups typically exfiltrate data before encrypting it, enabling double extortion: pay, or we publish your data publicly. Ransomware attacks on healthcare organizations have directly disrupted patient care, with documented cases of delayed surgeries and diverted ambulances.[10]

**Spyware** collects information from an infected system without the user's knowledge, including keystrokes, screenshots, and browsing history.

**Rootkits** hide malware from the operating system and security software by operating at a privileged level below where most security tools can inspect.

**Remote Access Trojans (RATs)** give attackers persistent, covert remote control of a compromised system. They can capture keystrokes, activate cameras and microphones, and move laterally through networks.

**Bots** are compromised systems controlled remotely, often used as part of a botnet to conduct DDoS attacks, send spam, or mine cryptocurrency without the owner's knowledge.

**Preventing malware** requires a layered approach: keeping systems and software updated, using endpoint detection and response (EDR) tools rather than legacy antivirus alone, restricting user privileges, and training users to recognize social engineering.

---

## Encryption

Encryption converts readable data into an unreadable format using a mathematical algorithm and a key. Only someone with the correct key can decrypt and read the data. It is the foundational technology for protecting data in transit and at rest.

**Symmetric encryption** uses a single key for both encryption and decryption. AES (Advanced Encryption Standard), standardized by NIST in 2001, is the most widely deployed symmetric algorithm in use today.[11]

**Asymmetric encryption** uses a key pair: a public key that anyone can use to encrypt data, and a private key that only the owner can use to decrypt it. HTTPS, the secure version of web browsing, uses asymmetric cryptography to establish secure sessions. RSA and elliptic curve cryptography (ECC) are the dominant asymmetric algorithms.[12]

**Full disk encryption** protects all data on a storage device. If a laptop is stolen but the disk is encrypted, the data is unreadable without the correct credentials. BitLocker (Windows) and FileVault (macOS) implement full disk encryption at the operating system level. Modern Android and iOS devices encrypt storage by default once a PIN or passphrase is set.[13]

**End-to-end encryption (E2EE)** ensures that only the communicating parties can read messages. Not the service provider, not anyone intercepting traffic. Signal implements E2EE using the Double Ratchet Algorithm, which provides both forward secrecy and break-in recovery.[14]

---

## The Tools of the Trade

Security practitioners use a core set of tools for both offensive and defensive work. You will encounter these throughout any technical certification or training path.

**Nmap** (Network Mapper) is an open-source tool for network discovery and security auditing. It identifies hosts, services, operating systems, and open ports on a network. Nmap is where most network-based assessments begin.[15]

**Metasploit** is an open-source penetration testing framework maintained by Rapid7. It provides a library of known exploits and a platform for developing and executing attacks in authorized testing environments. OSCP candidates spend significant time learning Metasploit.[16]

**Burp Suite**, developed by PortSwigger, is the standard tool for web application security testing. It intercepts and modifies HTTP/S traffic, scans for vulnerabilities, and enables manual testing of web application attack surfaces. Every web application penetration tester uses it.[17]

**Wireshark** is an open-source network protocol analyzer. It captures and inspects network traffic in real time, allowing analysts to diagnose network problems, analyze protocol behavior, and investigate suspicious traffic patterns.[18]

All four tools are freely available (Burp Suite has a free community edition). All appear in professional certifications including the OSCP, Security+, and CEH. They are where any technical home lab should start.

---

## Digital Forensics

Digital forensics is the application of scientific investigation methods to digital evidence. When a breach occurs, forensic investigators determine what happened, how the attacker gained access, what data was touched, and what evidence can be preserved for legal proceedings or internal use.

The Locard Exchange Principle, established by forensic scientist Edmond Locard, holds that every contact leaves a trace.[19] In digital forensics, this means attackers leave artifacts: log entries, registry modifications, network connections, file system changes, and memory residue that forensic tools can recover and analyze.

Key principles:

**Chain of custody**: A documented record of who handled evidence and when, ensuring its integrity throughout a legal process. If chain of custody is broken, evidence may be inadmissible.

**Evidence preservation**: Creating exact forensic copies (disk images) of storage media before analysis, preserving the original evidence unchanged. Analysis is performed on the copy, not the original.

**Hash verification**: Using cryptographic hash functions (MD5, SHA-256) to create a fingerprint of evidence. If the hash of a disk image matches the hash of the original drive, the image is demonstrably unchanged.

A failure to follow proper forensic procedures can render evidence inadmissible in court. Organizations planning legal action after a breach should preserve evidence before attempting remediation and involve legal counsel early in the process.

---

## References

[1] Gibson, William (1984). *Neuromancer*. Ace Books. ISBN 0-441-56956-0.

[2] Von Solms, Rossouw; van Niekerk, Johan (2013). "From information security to cyber security". *Computers & Security*. 38: 97–102. doi:10.1016/j.cose.2013.04.004.

[3] Verizon (2023). *2023 Data Breach Investigations Report*. Verizon Business. Retrieved from verizon.com/business/resources/reports/dbir/

[4] Mandia, Kevin (2020). "FireEye Shares Details of Recent Cyber Attack, Actions to Protect Community". FireEye. Retrieved 2024.

[5] Federal Bureau of Investigation (2023). *2022 Internet Crime Report*. Internet Crime Complaint Center (IC3). Retrieved from ic3.gov/Media/PDF/AnnualReport/2022_IC3Report.pdf

[6] Kolias, C.; Kambourakis, G.; Stavrou, A.; Voas, J. (2017). "DDoS in the IoT: Mirai and Other Botnets". *Computer*. 50 (7): 80–84. doi:10.1109/MC.2017.201.

[7] OWASP (2021). "OWASP Top Ten 2021". Open Web Application Security Project. Retrieved 2024 from owasp.org/www-project-top-ten/

[8] Digital Shadows (2020). *From Exposure to Takeover: The 15 Billion Stolen Credentials Allowing Account Takeover*. Digital Shadows. Retrieved 2024.

[9] Ehrenfeld, Jesse M. (2017). "WannaCry, Cybersecurity and Health Information Technology: A Time to Act". *Journal of Medical Systems*. 41 (7): 104. doi:10.1007/s10916-017-0752-1.

[10] Lemos, Robert (2020). "Ransomware's Dangerous New Trick Is Double-Encrypting Your Data". *Wired*. Retrieved 2024 from wired.com.

[11] NIST (2001). "Advanced Encryption Standard (AES)". *FIPS Publication 197*. National Institute of Standards and Technology. doi:10.6028/NIST.FIPS.197.

[12] Rescorla, Eric (2018). "The Transport Layer Security (TLS) Protocol Version 1.3". *RFC 8446*. Internet Engineering Task Force. doi:10.17487/RFC8446.

[13] Apple Inc. (2023). *Apple Platform Security*. Apple Inc. Retrieved 2024 from support.apple.com/guide/security/

[14] Marlinspike, Moxie; Perrin, Trevor (2016). "The Double Ratchet Algorithm". Signal Foundation. Retrieved 2024 from signal.org/docs/specifications/doubleratchet/

[15] Lyon, Gordon F. (2009). *Nmap Network Scanning: The Official Nmap Project Guide to Network Discovery and Security Scanning*. Insecure.Com LLC. ISBN 978-0-9799587-1-7.

[16] Kennedy, David; O'Gorman, Jim; Kearns, Devon; Aharoni, Mati (2011). *Metasploit: The Penetration Tester's Guide*. No Starch Press. ISBN 978-1-59327-288-3.

[17] PortSwigger (2023). "Burp Suite Documentation". PortSwigger Web Security. Retrieved 2024 from portswigger.net/burp/documentation

[18] Combs, Gerald (2023). "Wireshark User's Guide". Wireshark Foundation. Retrieved 2024 from wireshark.org/docs/wsug_html_chunked/

[19] Locard, Edmond (1930). "The Analysis of Dust Traces: Part I". *The American Journal of Police Science*. 1 (3): 276–298. doi:10.2307/1147011.

---

## Further Reading

**NIST Computer Security Resource Center** (csrc.nist.gov): The authoritative US government source for cybersecurity standards, guidelines, and publications. The NIST Cybersecurity Framework and Special Publication 800 series are required reading for anyone working in the field professionally. [csrc.nist.gov](https://csrc.nist.gov)

**Verizon Data Breach Investigations Report** (verizon.com/business/resources/reports/dbir/): Published annually, this is the most widely cited source for real-world data on breach causes, attack types, and affected industries. Based on analysis of tens of thousands of confirmed incidents. Required reading for defensive security practitioners.

**OWASP Top 10** (owasp.org/www-project-top-ten/): The standard reference for the most critical web application vulnerabilities, updated every few years based on industry data. Required reading for anyone doing application security work, offensive or defensive.

**Schneier on Security** (schneier.com): Bruce Schneier covers cryptography, security policy, and threat analysis with depth and clarity. Free, updated regularly, and a reliable signal in a noisy field.

**Mitnick, Kevin D. (2011). *The Art of Intrusion*. Wiley. ISBN 978-0-7645-6959-3**: A collection of real-world social engineering and hacking case studies. More engaging than most technical texts and gives genuine insight into how attackers think and operate.

---

*Questions about what you just read? Want to go deeper on a specific topic? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). And if this book helped, contribute back — fix something, improve something, add a resource you found useful.*
