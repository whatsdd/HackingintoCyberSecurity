# Skills and Certifications

Knowing which pillar interests you is one thing. Knowing what to actually build, and in what order, is another. This section covers the skills that matter regardless of specialization, the ones that separate the pillar paths, and a clear certification roadmap so you're not paralyzed by the dozens of credentials the industry throws at you.

---

## The Foundation Everyone Needs

There are skills that show up in every pillar of cybersecurity. These aren't optional, and building them early accelerates everything else.

**Networking**

Networks are the battlefield. Understanding how data moves, how protocols work, and where traffic can be intercepted, redirected, or inspected is the substrate everything else sits on. If you don't understand TCP/IP, DNS, HTTP/S, routing, and firewall rules, you can't protect a network or attack one meaningfully.

Start with CompTIA Network+ as a structured way to build this. Then read and re-read the relevant chapters whenever a concept is fuzzy. Networking is the one area where "good enough" comes back to haunt you.

**Linux**

The internet runs on Linux. Most servers run Linux. Most security tools run on Linux. Most CTF challenges run on Linux. Every penetration testing distribution (Kali, Parrot, BlackArch) is Linux.

You need to be comfortable on the command line. Not proficient in kernel development, just fluent in daily use: navigating the filesystem, managing processes, reading and writing files, piping commands together, understanding permissions. Spend time in a terminal every day until it feels natural. It won't take as long as you think.

**Scripting**

You don't need to be a software developer. You need to be able to write a script that automates a repetitive task, parse output from a tool and do something useful with it, and read someone else's code and understand roughly what it does.

Python is the standard. It's readable, well-documented, has libraries for everything security-related, and is what most security tools are built on or extended with. An afternoon a week on Python, focused on practical exercises rather than theory, is enough to build useful scripting skills within a few months.

**Understanding how attacks work**

Even if you never want to do offensive work, understanding how attacks happen makes you a dramatically better defender. If you've never seen a SQL injection work, you'll miss it in a log. If you don't understand how phishing campaigns are constructed, you won't know what indicators to look for.

The OWASP Top 10 is the standard reference for web application vulnerabilities. Read it. Then practice in a legal environment (TryHackMe or a deliberately vulnerable application like DVWA) until you can explain each vulnerability clearly without looking it up.

**Written communication**

Every single job in cybersecurity requires writing. Penetration test reports. Incident reports. Risk assessments. Executive summaries. Policy documents. Email chains explaining a critical vulnerability to someone who doesn't know what a vulnerability is.

Your writing quality directly affects your career trajectory. Clear, concise, technically accurate writing is rare. If you develop it early, it sets you apart. If you neglect it, it caps your growth.

---

## Skills That Depend On Your Pillar

Beyond the foundation, each pillar has its own technical depth requirements.

**Offensive Security:** Deep knowledge of specific vulnerability classes (web, network, Active Directory, cloud). Familiarity with tools like Metasploit, Burp Suite, Nmap, Nessus, Cobalt Strike. Understanding of programming and scripting beyond basic Python (Bash, PowerShell, sometimes C or Go for custom tooling). Report writing that is clear enough that a developer can reproduce the finding and fix it without your help.

**Defensive Security:** SIEM platforms (Splunk, Microsoft Sentinel, Elastic) for log analysis and correlation. Endpoint detection tools (CrowdStrike, SentinelOne, Carbon Black). Network traffic analysis. Familiarity with attacker TTPs (tactics, techniques, and procedures), particularly the MITRE ATT&CK framework, which maps real-world adversary behavior and is used in nearly every mature SOC.

**Security Engineering:** Cloud platforms deeply, not just surface-level certification knowledge. Infrastructure as code (Terraform, Ansible). Identity and access management design (SAML, OAuth, directory services). Network architecture principles. Secure software development practices. The ability to evaluate vendor security tools critically rather than just following marketing claims.

**GRC:** The major compliance frameworks inside out: what ISO 27001 requires, how SOC 2 audits work, what NIST CSF recommends, what GDPR mandates. Risk quantification methodologies. Policy and procedure writing. Audit preparation and evidence management. The ability to communicate risk in business terms, not technical jargon.

---

## The Certification Roadmap

The cybersecurity certification landscape is genuinely overwhelming. There are hundreds of credentials, and vendors have a financial interest in convincing you that their specific certification is essential. Here's a clear-headed view of what actually matters.

**Phase 1: Foundation (before your first job)**

These certifications exist to prove foundational knowledge to employers when you don't have a work history to point to yet.

*CompTIA Network+* builds the networking fundamentals that everything else depends on. If you already have a networking background, you may be able to skip it. If you don't, it's worth the time.

*CompTIA Security+* is the most widely recognized entry-level cybersecurity certification in the industry. It's vendor-neutral, covers a broad range of foundational topics, and is required or preferred by a large number of employers, particularly in government, defense, and enterprise environments. Get this first, full stop.

**Phase 2: Specialization (once you've chosen a pillar)**

*For Offensive Security:*
The eJPT (eLearnSecurity Junior Penetration Tester) is an affordable, hands-on certification that proves you can perform basic penetration testing tasks. Good first step.
CompTIA PenTest+ covers broader offensive concepts.
The OSCP (Offensive Security Certified Professional) is the real target. It requires passing a 24-hour hands-on lab exam where you're expected to compromise multiple machines by exploiting vulnerabilities. It's difficult, it's expensive, and employers know it's difficult. Earning it is a genuine signal of capability.

*For Defensive Security:*
CompTIA CySA+ is focused specifically on threat detection and analysis.
The BTL1 (Blue Team Level 1) from Security Blue Team is affordable, highly practical, and very well-regarded for entry-level defensive work.

*For Security Engineering:*
AWS Certified Security Specialty, Azure Security Engineer Associate, or Google Professional Cloud Security Engineer, depending on the cloud platform your target employers use.
The CCSP (Certified Cloud Security Professional) is vendor-neutral and respected for cloud security roles.

*For GRC:*
CISM (Certified Information Security Manager) and CRISC (Certified in Risk and Information Systems Control) are the most respected credentials in this space. Both require work experience, so they're mid-career targets rather than entry-level ones. Start with Security+ and build toward them.

**Phase 3: Senior level**

CISSP (Certified Information Systems Security Professional) is the industry's senior-level credential. It covers eight domains of security knowledge broadly and requires five years of work experience to hold. It's recognized everywhere and signals serious professional credibility. Most people pursue it after a few years of mid-level experience.

**One important warning:** don't collect certifications as a substitute for skills. A resume full of credentials and no demonstrable ability is easy to spot in an interview. The certifications should confirm capabilities you already have, not paper over gaps you haven't addressed.

---

## Don't Fall for the Expensive Cert Trap

The cybersecurity training industry is enormous and very good at making you feel like you need to spend thousands of dollars before anyone will hire you. You don't.

Some specific things to watch out for:

**SANS courses** are excellent. They're also $5,000 to $7,000 per course. SANS is worth it later in your career when an employer pays for it. It is not where you should start, and you should not go into debt for it at the entry level.

**EC-Council's CEH** (Certified Ethical Hacker) costs around $2,000 and is widely considered mediocre by working professionals. It's a multiple-choice exam testing memorized definitions, not actual hacking ability. Employers in the know are aware of this. A completed OSCP or even a solid TryHackMe profile will impress a technical hiring manager far more.

**Bootcamp programs** promising to make you job-ready in 12 weeks for $15,000 to $20,000 should be approached with serious skepticism. Some are fine. Many are not. Research outcomes data, not marketing claims. Talk to graduates before paying.

**CISSP prep courses** costing $3,000 to $5,000 are largely unnecessary. The official ISC2 study guide plus a few practice exam platforms costs under $100. The exam itself is the investment.

The pattern is the same across all of them: vendors benefit when you believe credentials require expensive training. That's not always true.

What actually signals competence to hiring managers, especially technical ones: a working project on GitHub. Not an impressive-sounding project. A working one. Something you built, that runs, that solves a problem. One real project tells me more about a candidate than five vendor certifications.

If you don't have a GitHub profile yet, that's your first task after reading this. It doesn't have to be impressive. It has to exist and show that you do things, not just study things.

---

## How Long Does This Actually Take?

Realistically, starting from no technical background:

Six to twelve months of focused effort gets most people to their first entry-level job. That means studying for CompTIA Security+ (roughly 60 to 100 hours of preparation), completing a structured TryHackMe or similar learning path, and building a portfolio of documented practice work you can discuss.

If you already have a networking or IT background, you can compress that significantly. Many people with solid IT experience land their first security role in three to six months.

The people who take longer are usually the ones who spread their attention across too many certifications at once, or who study in isolation without building hands-on practice alongside the theory.

---

## Further Reading

**Professor Messer's CompTIA Study Materials** (professormesser.com): Free, comprehensive video courses for CompTIA A+, Network+, Security+, and CySA+. The Network+ and Security+ courses are widely regarded as among the best free study resources available. [professormesser.com](https://www.professormesser.com)

**CompTIA Official Certifications** (comptia.org): The authoritative source for exam objectives, pricing, and approved study materials. Always check here for the latest exam version before buying study materials. [comptia.org](https://www.comptia.org)

**Offensive Security (OSCP and related)** (offsec.com): The home of the OSCP certification and the Proving Grounds practice labs. Their training philosophy, learning by doing, is worth understanding even if you're not pursuing their certifications. [offsec.com](https://www.offsec.com)

**OWASP Top 10** (owasp.org/www-project-top-ten): The definitive reference for the ten most critical web application security risks. Required reading for anyone interested in application security, offensive or defensive. Updated every few years based on current vulnerability data. [owasp.org](https://owasp.org/www-project-top-ten/)

**ISC2 CISSP** (isc2.org/certifications/cissp): The official source for CISSP exam content, experience requirements, and the Common Body of Knowledge (CBK) domains. The CBK domains are a useful map of what a senior security professional is expected to understand broadly.

**ISACA Certifications** (isaca.org): The home of CISM, CRISC, and CISA. If GRC is your pillar, ISACA's certification pathways are where you'll eventually land. [isaca.org](https://www.isaca.org)

---

*Have questions, want feedback on your GitHub or LinkedIn, or just need a nudge in the right direction? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out directly on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). And if this book helped you, contribute back — that commit on your GitHub is worth more than you think.*
