# Hacking Skills

Nobody becomes a penetration tester by reading about it. You build the skills by breaking things, fixing them, and breaking them again in environments you control. This chapter covers what you actually need to learn, in roughly the order you should learn it.

There is no shortcut here. The people who are genuinely good at offensive security have put in thousands of hours on the fundamentals. What separates them from people who plateau early is not raw intelligence -- it is having built a real foundation before picking up attack tools.

---

## Start With the Fundamentals, Not the Tools

A common mistake: people download Kali Linux, run Nmap against something, and call themselves hackers. Nmap tells you a port is open. Knowing what to do with that information requires understanding why that port exists, what protocol is listening on it, and what kinds of mistakes implementations of that protocol tend to make.

The tools are multipliers. They amplify what you know. They cannot substitute for knowing.

Build in this order:

1. Networking
2. Operating systems (Linux first, then Windows)
3. Programming and scripting
4. Web application fundamentals
5. Attack methodology
6. Specialization

---

## Networking

Most attacks travel over networks. Most defenses live at network boundaries. If you do not understand how data moves between systems, you will not understand why most exploits work.

You need to know:

**TCP/IP and the OSI model.** Understand what happens at each layer when you send an HTTP request. Know how IP fragmentation works, how TCP handles connection state, why UDP is different [1].

**DNS.** Understand how domain names resolve to IP addresses. DNS is a surprisingly fertile attack surface -- zone transfers, DNS rebinding, DNS cache poisoning, and subdomain takeover are all real attack classes [2].

**HTTP and HTTPS.** You will attack web applications constantly. Understand the full request/response cycle, how cookies and sessions work, what TLS actually does, and the difference between HTTP/1.1 and HTTP/2 at the protocol level.

**Common protocols.** Know SSH, FTP, SMTP, SMB, LDAP, Kerberos. Not deeply at first -- just enough to recognize them in a port scan and know what questions to ask.

**Practical tool:** Wireshark. Capture your own traffic and read it. Watch a TLS handshake. Watch a three-way TCP handshake. Watch DNS queries resolve in real time. Passive study of real traffic teaches more than any textbook [3].

---

## Operating Systems

**Linux is non-negotiable.** Most servers run Linux. Most security tools are designed for Linux. Kali Linux ships with the majority of the tools you will use, but do not start with Kali. Start with Ubuntu or Debian. Learn to install packages, manage permissions, edit files from the command line, read logs, write basic shell scripts, and understand how processes and users interact [4].

Key Linux concepts for security work:

- File permissions and setuid/setgid
- The /proc filesystem
- Process management and signals
- Network configuration and iptables
- Cron jobs and persistence mechanisms
- Package managers and software repositories

**Windows matters more than people admit.** Most enterprise environments run Windows Active Directory. Many of the most impactful attacks in penetration testing involve Kerberos, NTLM, SMB, and Group Policy -- all Windows-specific technology. Learn enough to navigate a Windows domain: understand users and groups, how authentication flows, where credentials are cached, and how Group Policy Objects work [5].

---

## Programming and Scripting

You do not need to be a software engineer. You do need to write code.

**Python** is the primary scripting language in security. Most public exploits, automation tools, and custom attack scripts are in Python. You need to read it fluently and write it functionally -- that means file I/O, network sockets, HTTP requests, parsing JSON and XML, and basic string manipulation [6].

**Bash scripting** is unavoidable on Linux. Learn to chain commands, write loops, handle arguments, and redirect output. Most of your day-to-day automation on the command line will be one-liners or short scripts.

**Understanding compiled languages.** You do not need to write production C, but you need to read it well enough to understand what a buffer overflow is and why it happens. A few dozen hours reading C code and studying memory layout will pay dividends in understanding vulnerability classes at a depth that Python alone cannot give you.

**JavaScript** is increasingly important for web application testing. You need to understand how the DOM works, how JavaScript interacts with the browser security model, and what XSS actually does in execution.

A practical goal: by the time you apply for your first penetration testing role, you should be able to write a port scanner from scratch in Python without looking anything up. It does not have to be fast or elegant. It should work.

---

## Web Application Fundamentals

Web applications are the most common attack surface in modern penetration testing. The OWASP Top 10 -- the standard reference for web vulnerability categories -- covers injection, broken authentication, insecure direct object references, security misconfigurations, XSS, and more [7].

Before you exploit web vulnerabilities, understand how web applications are built:

- How authentication and session management work
- How databases interact with web applications (and why SQL injection is possible)
- How browsers enforce the same-origin policy
- How cookies, localStorage, and sessionStorage differ
- How modern frameworks (React, Next.js, Django) structure requests and responses

Burp Suite is the essential tool. The free community edition covers basic interception and repeater functionality. Burp Pro adds scanner capability and is worth the investment eventually, but start with the free version and learn to manually manipulate requests [8].

---

## The Attack Methodology

Attacks follow a pattern. Knowing the pattern helps you both execute offensively and defend against it.

**Reconnaissance** is information gathering before you touch the target. Passive recon uses public sources: WHOIS records, certificate transparency logs, job postings (which reveal technology stack), LinkedIn (which reveals employee names and technologies they list as skills), and tools like Shodan and Censys to find internet-exposed infrastructure [9].

Active recon touches the target: DNS enumeration, port scanning, service fingerprinting. Nmap is the standard. Learn its output cold -- open/closed/filtered states, version detection, script engine usage [10].

**Scanning and enumeration** goes deeper into discovered services. Open port 443? Enumerate subdomains, identify the server software and version, check for known CVEs, spider the application for hidden paths. Each open service is a potential entry point.

**Exploitation** is using a discovered vulnerability to gain access. This is rarely dramatic. In most real engagements, entry comes from one of a short list of recurring failures: default credentials, unpatched software, SQL injection in a login form, or phishing (which is technically social engineering but lands in the same phase).

**Post-exploitation** is what you do after access. In a real attack, post-exploitation is where the damage happens: lateral movement to other systems, privilege escalation from regular user to administrator, credential harvesting, and data exfiltration. In a penetration test, you demonstrate capability and stop. You document every step.

**Pivoting** is using a compromised system as a launch point into network segments that were not directly accessible. A web server in the DMZ can become a bridge into internal systems that have no direct internet exposure.

**Reporting** is the product. Everything else is how you earn the right to write it. A good penetration testing report has an executive summary (one to two pages, written for a CISO who will not read the technical details), a technical findings section (severity, description, evidence, reproduction steps), and prioritized remediation recommendations [11].

---

## Practice Environments

**Hack The Box** (hackthebox.com) is the gold standard for intermediate-to-advanced practice. Machines range from beginner to insane difficulty. The community writeups (after you have tried and failed) are excellent learning resources. Active machines release every Saturday; retired machines are accessible to VIP subscribers [12].

**TryHackMe** (tryhackme.com) is better for beginners. Guided learning paths with structured rooms walk you through concepts before asking you to apply them independently. The "Jr Penetration Tester" path is a reasonable starting curriculum [13].

**VulnHub** provides downloadable virtual machine images you can run locally. No internet required, no subscription. Older machines are often simpler, which makes them good for practicing fundamentals.

**DVWA (Damn Vulnerable Web Application)** is a deliberately insecure PHP application you run locally. It lets you practice every OWASP Top 10 category in an environment you cannot break in any meaningful way. Essential for web application learning [14].

**Your own home lab** is irreplaceable. A spare machine or a laptop running VirtualBox or VMware can host a small network of virtual machines: a Kali attacker, a Windows Server domain controller, a Ubuntu web server, and a vulnerable machine. Building infrastructure you then attack teaches you both sides.

---

## Certifications for Offensive Security

Covered in more depth in Chapter 1, but the relevant certifications for offensive security specifically:

**CompTIA Security+** is the entry baseline. Most employers want to see it. It is not offensive-focused, but it proves foundational knowledge.

**eJPT (eLearnSecurity Junior Penetration Tester)** is the best starting point for practical offensive certification. Inexpensive, practical exam format, respected as an entry-level credential.

**PNPT (Practical Network Penetration Tester)** from TCM Security is highly practical and has become well-regarded in the industry. The course content is excellent even if you never take the exam.

**OSCP (Offensive Security Certified Professional)** from Offensive Security is the gold standard for hands-on penetration testing. It is a 24-hour practical exam where you must compromise a series of machines in a lab environment and write a professional report afterward. It is hard. It is expensive (~$1,500). It is worth it if you have the prerequisite skills. Attempting OSCP before you have solid networking, Linux, and scripting fundamentals is a waste of money [15].

Do not start with OSCP. Build the foundation first. Most people who pass OSCP on their first attempt have spent six to twelve months doing Hack The Box machines, building labs, and reading before they sit the exam.

---

## CTFs as a Training Ground

Capture The Flag competitions are structured hacking challenges. You find a hidden string (the "flag") by exploiting a vulnerability in a target system or solving a puzzle. CTFs cover web exploitation, binary exploitation (pwn), reverse engineering, cryptography, forensics, and OSINT.

CTFs are valuable for three reasons. First, they teach you specific techniques in isolation -- a CTF web challenge might require exactly one SQLi variant, which forces you to understand it deeply. Second, they give you portfolio material -- writing a clear CTF walkthrough demonstrates both technical skill and the ability to communicate findings, which is directly relevant to penetration testing. Third, the community around CTFs is excellent and often the fastest way to level up quickly [16].

CTFtime.org lists upcoming competitions. PicoCTF is the best starting point for absolute beginners. After that, try HackTheBox challenges (separate from the main machines) and TryHackMe CTF rooms.

A separate chapter in this book covers CTFs in depth.

---

## Building a Public Portfolio

GitHub matters. A repository with your custom scripts, CTF writeups, and home lab documentation is evidence that you know what you are doing. It shows hiring managers things a certificate cannot: that you build things, that you can explain your thinking, and that you work consistently over time.

Writeups are particularly valuable. When you solve a CTF challenge or a Hack The Box machine, write a clear technical walkthrough. Explain what you found, how you approached it, what failed before you found what worked, and how the vulnerability could be remediated. This is exactly what a penetration testing report looks like, and a portfolio of writeups is direct evidence that you can produce one.

---

## Further Reading

- OWASP Web Security Testing Guide: [https://owasp.org/www-project-web-security-testing-guide/](https://owasp.org/www-project-web-security-testing-guide/)
- TCM Security courses (affordable, practical): [https://academy.tcm-sec.com/](https://academy.tcm-sec.com/)
- PortSwigger Web Security Academy (free, excellent for web): [https://portswigger.net/web-security](https://portswigger.net/web-security)
- *The Hacker Playbook 3* by Peter Kim: practical attack scenarios
- LiveOverflow YouTube channel: binary exploitation and CTF methodology explained clearly

---

## References

[1] Forouzan, B. A. (2013). *Data Communications and Networking* (5th ed.). McGraw-Hill Education. ISBN 978-0073376226.

[2] Dafydd, S., & Pinto, M. (2011). *The Web Application Hacker's Handbook: Finding and Exploiting Security Flaws* (2nd ed.). Wiley. ISBN 978-1118026472.

[3] Combs, G., & the Wireshark Team. (2023). *Wireshark User's Guide*. The Wireshark Foundation. Retrieved from https://www.wireshark.org/docs/wsug_html/

[4] Shotts, W. (2019). *The Linux Command Line: A Complete Introduction* (2nd ed.). No Starch Press. ISBN 978-1593279523.

[5] Metcalf, S. (2015). *Kerberos & Attacks 101*. Active Directory Security. Retrieved from https://adsecurity.org/?p=2011

[6] Seitz, J. (2021). *Black Hat Python: Python Programming for Hackers and Pentesters* (2nd ed.). No Starch Press. ISBN 978-1718501126.

[7] OWASP Foundation. (2021). *OWASP Top Ten 2021*. Open Web Application Security Project. Retrieved from https://owasp.org/www-project-top-ten/

[8] PortSwigger. (2023). *Burp Suite Documentation*. PortSwigger Web Security. Retrieved from https://portswigger.net/burp/documentation

[9] Shodan.io. (2023). *Shodan: The Search Engine for the Internet of Things*. Retrieved from https://www.shodan.io/

[10] Lyon, G. (2009). *Nmap Network Scanning: The Official Nmap Project Guide to Network Discovery and Security Scanning*. Insecure.com LLC. ISBN 978-0979958717. Retrieved from https://nmap.org/book/

[11] Weidman, G. (2014). *Penetration Testing: A Hands-On Introduction to Hacking*. No Starch Press. ISBN 978-1593275648.

[12] Hack The Box. (2023). *Hack The Box: Cybersecurity Training Platform*. Retrieved from https://www.hackthebox.com/

[13] TryHackMe. (2023). *TryHackMe: Learn Cybersecurity*. Retrieved from https://tryhackme.com/

[14] Ryan Dewhurst. (2015). *Damn Vulnerable Web Application (DVWA)*. GitHub. Retrieved from https://github.com/digininja/DVWA

[15] Offensive Security. (2023). *PEN-200: Penetration Testing with Kali Linux (OSCP)*. Offensive Security. Retrieved from https://www.offensive-security.com/pwk-oscp/

[16] Chung, S. P., Xu, W., & Lee, W. (2013). Finding the needle: Suppression of false alarms in large intrusion detection data sets. *Proceedings of the IEEE International Symposium on Software Reliability Engineering*, 2013. doi:10.1109/ISSRE.2013.6698933

---

*This chapter is part of Hacking into Cybersecurity, an open-source guide maintained by the community.*

*Connect with the author:*
- *LinkedIn: [Ahmad Abdur Rehman](https://www.linkedin.com/in/ahmadscience/)*
- *Discord: [Join the community](https://discord.gg/vkXWVFdFe)*
