# Introduction to Cyber Security

> "Cyberspace. A consensual hallucination experienced daily by billions of legitimate operators."
>
> -- William Gibson, *Neuromancer* (1984) [1]

Gibson wrote that as science fiction. Today it describes infrastructure that moves money, delivers medicine, controls power grids, and carries private conversations for half the planet. The gap between the fiction and the reality is that nobody designed this infrastructure to be secure. It was designed to be useful. Security came later, always running behind.

That is the central tension in cybersecurity: systems built for openness, retrofitted with protection, defended by professionals who are always outnumbered and outpaced. Understanding that tension is where the field begins.

---

## What Cybersecurity Actually Is

Cybersecurity is the practice of protecting systems, networks, and data from unauthorized access, damage, or attack. That definition is technically accurate but undersells the scope. Modern cybersecurity covers everything from consumer smartphones to hospital networks to the industrial control systems that manage water treatment, power generation, and air traffic. The field exists because everything of value now lives in or passes through digital infrastructure -- and digital infrastructure has vulnerabilities, not as an exception, but as a structural property.

Technically, cybersecurity is a subset of information security that specifically addresses electronic systems and the threats that target them. Information security is the broader discipline: protecting information in any format against any threat, including paper records, verbal communication, and physical assets.[2] In practice the two terms are used interchangeably, and understanding both is foundational.

What distinguishes cybersecurity from almost every other engineering discipline is that the adversary is intelligent. A bridge engineer does not worry that gravity will study the bridge's design and adapt. A cybersecurity professional does. Attackers learn, evolve, share techniques, and specifically work to circumvent whatever controls exist. That dynamic never stops, which is why the field never stagnates.

---

## The Threat Landscape

Not every attacker is the same. Conflating a ransomware criminal with a nation-state operator leads to defenses calibrated for the wrong threat. The threat landscape contains distinct actors with distinct motivations, resources, and patience.

| Actor | Motivation | Sophistication | Typical Targets |
|---|---|---|---|
| Organized criminal groups | Financial gain | Moderate to high | Businesses of all sizes, healthcare, finance |
| Nation-state actors | Espionage, disruption | Very high | Government, defense, critical infrastructure |
| Hacktivists | Political or social agenda | Low to moderate | High-profile brands, governments |
| Insider threats | Financial gain, grievance, negligence | Varies | Employers, clients |
| Opportunistic attackers | Quick financial gain | Low | Anyone with exposed vulnerabilities |

The most common threat to most organizations is financially motivated crime. Ransomware, business email compromise, and payment fraud account for the overwhelming majority of incidents that security teams handle. The Verizon Data Breach Investigations Report, which analyzes tens of thousands of confirmed incidents annually, consistently shows that external financially motivated actors are responsible for the majority of confirmed breaches.[3]

Nation-state actors are the most sophisticated and the most patient. They operate on timelines measured in months or years. Their goal is usually intelligence collection rather than immediate financial return.

{% hint style="info" %}
**Case Study: SolarWinds (2020)**

Attackers attributed to Russian intelligence (SVR/APT29, known as Cozy Bear) compromised the software build pipeline of SolarWinds -- a widely used IT management company. A malicious update labelled SUNBURST was pushed to roughly 18,000 organizations, including the US Treasury, the Department of Homeland Security, and multiple Fortune 500 companies. Attackers had undetected access for months before FireEye discovered the intrusion while investigating their own breach.[4]

The lesson: the software supply chain itself is an attack surface. Every piece of software your organization trusts carries the security posture of every vendor in its supply chain.
{% endhint %}

---

## Common Attack Types

Understanding how attacks work is foundational to defending against them, regardless of which career path you pursue. These are not abstract categories -- they are documented techniques that appear in real incidents every day.

### Phishing and Social Engineering

Phishing is the most common initial access technique across industries and geographies. An attacker sends a message designed to appear trustworthy, tricking the recipient into clicking a link, opening an attachment, or surrendering credentials. Variants include:

- **Spear phishing** -- targeted at specific individuals, using personalized details scraped from LinkedIn, company websites, or prior data breaches
- **Whaling** -- spear phishing aimed at executives or board members
- **Vishing** -- voice phishing over phone calls, sometimes using AI-synthesized voices
- **Smishing** -- phishing via SMS

Business email compromise (BEC) is a financially devastating variant where attackers compromise or convincingly spoof a corporate email account to authorize fraudulent wire transfers. The FBI's Internet Crime Complaint Center recorded **$2.7 billion in BEC losses in 2022 alone** -- more than any other cybercrime category.[5]

{% hint style="warning" %}
**Why phishing keeps working:** Security controls can block known malicious URLs and attachments. They cannot block a well-crafted message sent from a legitimate email service, asking a real employee to perform a routine action. The human element is not a bug in the system -- it is an intended feature of how organizations function. Attackers exploit trust, urgency, and authority because those things work.
{% endhint %}

### Denial of Service

Denial of Service (DoS) and Distributed Denial of Service (DDoS) attacks overwhelm a system or network with traffic until it is unavailable to legitimate users. DDoS attacks use botnets -- networks of compromised devices -- to amplify volume far beyond what any single attacker could generate.

The 2016 Mirai botnet attack weaponized hundreds of thousands of insecure IoT devices (home routers, IP cameras, DVRs) to flood Dyn, a major DNS provider, with traffic. The result: Twitter, Reddit, GitHub, Netflix, the New York Times, and dozens of other major sites went offline for much of the US East Coast for hours.[6]

### Man-in-the-Middle (MitM)

MitM attacks intercept communications between two parties. The attacker positions themselves in the path of traffic, reading, modifying, or injecting messages without either party knowing. Encryption is the primary defense -- if traffic is encrypted end-to-end, interception yields only ciphertext.

### Injection Attacks

Injection attacks insert malicious code into inputs that an application passes to an interpreter. SQL injection targets database queries; command injection targets operating system calls; LDAP injection targets directory services. A successful SQL injection can expose entire databases, modify records, or grant administrative access.

SQL injection has appeared on the OWASP Top 10 list of critical web vulnerabilities for over fifteen years. In 2023, the MOVEit breach -- which exposed data from hundreds of organizations including government agencies across the US, UK, and Canada -- was traced to a SQL injection zero-day in the MOVEit Transfer software.[7]

### Credential Attacks

Credential attacks use stolen, guessed, or brute-forced credentials to gain access. Modern variants include:

- **Credential stuffing** -- testing combinations from previous data breaches against new services, exploiting password reuse
- **Password spraying** -- trying common passwords across many accounts to avoid lockouts
- **Brute force** -- exhaustively trying all combinations against a single account

With billions of credential pairs available on dark web markets from previous breaches, credential-based attacks are consistently the most common initial access vector in confirmed incidents.

---

## Malware: A Field Guide

Malware -- software designed to damage, disrupt, or gain unauthorized access to systems -- comes in distinct categories. Knowing the differences matters because they have different infection vectors, different objectives, and require different defenses.

| Type | How It Spreads | What It Does | Notable Example |
|---|---|---|---|
| **Virus** | Attaches to files; spreads when files are executed | Corrupts files, steals data, delivers payloads | ILOVEYOU (2000) -- $10B in damages |
| **Worm** | Self-replicates across networks without user action | Spreads rapidly, delivers payloads, consumes bandwidth | WannaCry (2017) -- 200,000+ systems in 150 countries |
| **Trojan** | Disguised as legitimate software; user installs it | Creates backdoor, downloads other malware | Emotet -- the world's most dangerous malware network until its 2021 takedown |
| **Ransomware** | Via phishing, RDP exposure, supply chain | Encrypts data, demands payment; often exfiltrates first | Colonial Pipeline (2021) -- US fuel supply disrupted, $4.4M ransom paid |
| **Spyware** | Bundled with software, phishing | Steals keystrokes, screenshots, credentials | FinFisher, Pegasus (nation-state spyware targeting journalists) |
| **Rootkit** | Delivered by other malware | Hides malware from OS and security tools | Necurs rootkit (used to protect massive botnet) |
| **RAT** | Phishing, watering holes | Persistent remote control of victim system | DarkComet, njRAT |
| **Bot** | Exploit kits, drive-by downloads | Becomes part of botnet for DDoS, spam, cryptomining | Mirai, Emotet |

{% hint style="danger" %}
**Ransomware and healthcare:** Ransomware attacks against hospitals have caused measurable harm to patients. A 2021 study published in *JAMA* found that hospitals under cyberattack experienced increased in-hospital mortality rates and longer lengths of stay. When a hospital in Düsseldorf, Germany was hit by ransomware in 2020 and had to divert emergency patients, a woman died during transfer to a more distant facility -- one of the first documented deaths directly linked to a cyberattack.[8]

This is not an abstraction. Malware kills people.
{% endhint %}

---

## Encryption

Encryption converts readable data (plaintext) into an unreadable format (ciphertext) using a mathematical algorithm and a key. Without the correct key, ciphertext is computationally infeasible to read. It is the foundational technology for protecting data in transit and at rest.

### Symmetric Encryption

Symmetric encryption uses a single key for both encryption and decryption. Both parties must share the key securely before communication can begin.

**AES (Advanced Encryption Standard)**, standardized by NIST in 2001 after a five-year international competition, is the most widely deployed symmetric algorithm in the world. AES-256 (a 256-bit key) is used to protect classified US government information.[9]

```
Key size: 128, 192, or 256 bits
Block size: 128 bits
Rounds: 10 (AES-128), 12 (AES-192), 14 (AES-256)
Status: Unbroken; considered quantum-resistant with 256-bit keys
```

### Asymmetric Encryption

Asymmetric encryption uses a mathematically linked key pair: a **public key** anyone can use to encrypt data, and a **private key** only the owner possesses to decrypt it. This solves the key distribution problem inherent in symmetric encryption.

Every time your browser shows a padlock in the address bar, asymmetric cryptography (typically RSA or elliptic curve) established the session. TLS 1.3, defined in RFC 8446 (2018), is the current standard -- it eliminated support for outdated and broken cipher suites from earlier versions.[10]

### Encryption in Practice

{% hint style="info" %}
**What encryption protects -- and what it does not:**

Encryption protects data from being read in transit or at rest. It does not protect against:
- An attacker who has access to the decryption key
- A compromised endpoint (if your device is infected, data can be captured before encryption)
- Implementation flaws in how encryption is applied
- Metadata (who communicated with whom, when, and how often)

Full disk encryption (BitLocker on Windows, FileVault on macOS, LUKS on Linux) protects against physical theft -- a stolen encrypted laptop is worthless to an attacker without the credentials. Modern Android and iOS devices encrypt storage by default once a PIN is set.[11]

End-to-end encryption (E2EE) in messaging apps like Signal ensures only the communicating parties can read messages -- not the provider, not law enforcement, not an interceptor. Signal's Double Ratchet Algorithm provides both forward secrecy (past sessions cannot be decrypted if a key is later compromised) and break-in recovery.[12]
{% endhint %}

---

## The Tools of the Trade

Security practitioners use a core set of tools for both offensive and defensive work. You will encounter these throughout any technical certification or training path. Learning them early -- in legal environments -- accelerates everything else.

### Nmap

Nmap (Network Mapper) is the standard tool for network discovery and security auditing. It identifies hosts, open ports, running services, and operating system versions across a network.

```bash
# Basic host discovery on a subnet
nmap -sn 192.168.1.0/24

# Service version detection on a target
nmap -sV -p 1-1000 192.168.1.100

# Aggressive scan with OS detection and script engine
nmap -A 192.168.1.100

# Output results to a file for reporting
nmap -oN scan_results.txt 192.168.1.0/24
```

Nmap is where most network-based assessments begin and where most network defenders look when mapping their own exposure.[13]

### Metasploit

Metasploit is an open-source penetration testing framework maintained by Rapid7. It provides a library of exploits, payloads, and auxiliary modules for authorized testing. OSCP candidates spend significant time learning its operation.

```bash
# Start the Metasploit console
msfconsole

# Search for a specific module
msf6 > search ms17-010

# Use EternalBlue exploit (the vulnerability WannaCry used)
msf6 > use exploit/windows/smb/ms17_010_eternalblue
msf6 exploit > set RHOSTS 192.168.1.100
msf6 exploit > run
```

{% hint style="warning" %}
Running Metasploit against systems you do not own or do not have written permission to test is a criminal offense in most jurisdictions. Always use it in a home lab, authorized penetration test, or practice platform like Hack The Box.
{% endhint %}

Metasploit's power for defenders is in understanding exactly what an attacker with this tool can do to unpatched systems.[14]

### Burp Suite

Burp Suite, developed by PortSwigger, is the standard tool for web application security testing. It acts as a proxy between your browser and the target, intercepting and allowing modification of every HTTP/S request and response.

```
Intercepted request:
POST /login HTTP/1.1
Host: target.com
Content-Type: application/x-www-form-urlencoded

username=admin&password=password123

→ Modified by tester to test SQL injection:
username=admin'--&password=anything
```

PortSwigger's free Web Security Academy (portswigger.net/web-security) is one of the best free training resources in cybersecurity and teaches Burp Suite through real-world web vulnerability labs.[15]

### Wireshark

Wireshark captures and inspects network traffic in real time. Analysts use it to diagnose network problems, analyze protocol behavior, and investigate suspicious traffic.

```
# Useful Wireshark display filters:
http                     # Show only HTTP traffic
tcp.port == 443          # Show only HTTPS traffic
ip.addr == 192.168.1.100 # Traffic to/from specific host
dns                      # Show only DNS queries
tcp.flags.syn == 1       # Show TCP connection initiations
```

Watching a TLS handshake, a DNS query, or a TCP three-way handshake live in Wireshark teaches more about networking than hours of reading.[16]

---

## Digital Forensics

When a breach occurs, someone has to figure out what happened. Digital forensics is the application of scientific investigation methods to digital evidence -- determining how an attacker gained access, what they did once inside, what data was touched, and what evidence can be preserved for legal proceedings.

The Locard Exchange Principle, established by forensic scientist Edmond Locard, holds that every contact leaves a trace.[17] In digital environments, attackers leave artifacts: log entries, registry modifications, network connection records, file system changes, deleted files recoverable from unallocated disk space, and memory residue that forensic tools can extract and analyze.

**Core principles every practitioner needs to understand:**

{% hint style="info" %}
**Chain of custody** is a documented record of who handled evidence and when. If the chain is broken -- if evidence was accessible to parties not documented in the record -- it may be inadmissible in court and worthless for legal proceedings.

**Evidence preservation** means creating forensic bit-for-bit copies (disk images) of storage media before any analysis. Analysis is performed on the copy. The original is preserved unchanged. Modifying the original, even just by booting from it, alters timestamps and file metadata.

**Hash verification** uses cryptographic hash functions (SHA-256 is the current standard; MD5 is considered weak but still used in some contexts) to create a fingerprint of evidence. If the hash of a disk image matches the hash of the original, the image is demonstrably unmodified. Courts accept this as proof of integrity.
{% endhint %}

Memory forensics has become increasingly important as attackers use fileless malware -- malicious code that runs entirely in RAM and leaves no files on disk. Tools like Volatility allow investigators to extract process lists, network connections, decryption keys, and injected code from memory images.

{% hint style="warning" %}
**A critical operational note:** Organizations planning legal action after a breach should involve legal counsel **before** beginning remediation. The instinct to clean up a compromised system immediately can destroy evidence needed for prosecution, insurance claims, or regulatory reporting. Preserve first. Remediate second.
{% endhint %}

---

## References

[1] Gibson, W. (1984). *Neuromancer*. Ace Books. ISBN 978-0-441-56956-4.

[2] Von Solms, R.; van Niekerk, J. (2013). From information security to cyber security. *Computers & Security*, 38, 97--102. doi:10.1016/j.cose.2013.04.004

[3] Verizon. (2024). *2024 Data Breach Investigations Report*. Verizon Business. Retrieved from https://www.verizon.com/business/resources/reports/dbir/

[4] Mandia, K. (2020, December 8). FireEye shares details of recent cyber attack, actions to protect community. *FireEye Blog*. Retrieved from https://www.fireeye.com/blog/products-and-services/2020/12/fireeye-shares-details-of-recent-cyber-attack-actions-to-protect-community.html

[5] Federal Bureau of Investigation. (2023). *2022 Internet Crime Report*. Internet Crime Complaint Center (IC3). Retrieved from https://www.ic3.gov/Media/PDF/AnnualReport/2022_IC3Report.pdf

[6] Kolias, C., Kambourakis, G., Stavrou, A., & Voas, J. (2017). DDoS in the IoT: Mirai and other botnets. *Computer*, 50(7), 80--84. doi:10.1109/MC.2017.201

[7] CISA. (2023, June 7). *#StopRansomware: CL0P Ransomware Gang Exploits CVE-2023-34362 MOVEit Vulnerability*. Cybersecurity and Infrastructure Security Agency. Retrieved from https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-158a

[8] Srinivasan, M., & Agrawal, A. (2021). Impact of cybersecurity on hospital mortality rates. *JAMA Open Network*, 2021. doi:10.1001/jamanetworkopen.2021.21204

[9] National Institute of Standards and Technology. (2001). *Advanced Encryption Standard (AES)*. FIPS Publication 197. doi:10.6028/NIST.FIPS.197

[10] Rescorla, E. (2018). *The Transport Layer Security (TLS) Protocol Version 1.3*. RFC 8446. Internet Engineering Task Force. doi:10.17487/RFC8446

[11] Apple Inc. (2024). *Apple Platform Security*. Apple Inc. Retrieved from https://support.apple.com/guide/security/welcome/web

[12] Marlinspike, M., & Perrin, T. (2016). *The Double Ratchet Algorithm*. Signal Foundation. Retrieved from https://signal.org/docs/specifications/doubleratchet/

[13] Lyon, G. F. (2009). *Nmap Network Scanning: The Official Nmap Project Guide to Network Discovery and Security Scanning*. Insecure.Com LLC. ISBN 978-0-9799587-1-7. Retrieved from https://nmap.org/book/

[14] Kennedy, D., O'Gorman, J., Kearns, D., & Aharoni, M. (2011). *Metasploit: The Penetration Tester's Guide*. No Starch Press. ISBN 978-1-59327-288-3.

[15] PortSwigger. (2024). *Web Security Academy*. PortSwigger Web Security. Retrieved from https://portswigger.net/web-security

[16] Combs, G., & the Wireshark Team. (2024). *Wireshark User's Guide*. The Wireshark Foundation. Retrieved from https://www.wireshark.org/docs/wsug_html/

[17] Locard, E. (1930). The analysis of dust traces: Part I. *The American Journal of Police Science*, 1(3), 276--298. doi:10.2307/1147011

---

## Further Reading

| Resource | What It Covers |
|---|---|
| [NIST Computer Security Resource Center](https://csrc.nist.gov) | Authoritative source for US cybersecurity standards and the SP 800 series |
| [Verizon DBIR](https://www.verizon.com/business/resources/reports/dbir/) | Best single source for real-world breach data; published annually |
| [OWASP Top 10](https://owasp.org/www-project-top-ten/) | Standard reference for critical web application vulnerabilities |
| [PortSwigger Web Security Academy](https://portswigger.net/web-security) | Free, hands-on web vulnerability training; among the best free resources in the field |
| [Schneier on Security](https://www.schneier.com) | Cryptography, security policy, and threat analysis from Bruce Schneier -- reliable signal in a noisy space |

---

*Questions about what you just read? Want to go deeper on a specific topic? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). And if this book helped, contribute back -- fix something, improve something, add a resource you found useful.*
