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

| Pillar | Key Tools and Skills |
|---|---|
| **Offensive Security** | Metasploit, Burp Suite, Nmap, Nessus, Cobalt Strike; Bash/PowerShell/Python; writing exploits; report writing that a developer can act on |
| **Defensive Security** | Splunk, Microsoft Sentinel, Elastic (SIEM); CrowdStrike, SentinelOne, Carbon Black (EDR); network traffic analysis; MITRE ATT&CK framework |
| **Security Engineering** | Cloud platforms (AWS/Azure/GCP); Terraform, Ansible (IaC); SAML, OAuth, directory services (IAM); secure SDLC; vendor evaluation |
| **GRC** | ISO 27001, SOC 2, NIST CSF, GDPR, HIPAA (frameworks); risk quantification; policy and procedure writing; audit evidence management |

---

## The Certification Roadmap

The cybersecurity certification landscape is genuinely overwhelming. There are hundreds of credentials, and vendors have a financial interest in convincing you that their specific certification is essential. Here's a clear-headed view of what actually matters.

### Phase 1: Foundation (before your first job)

These certifications exist to prove foundational knowledge to employers when you don't have a work history to point to yet.

| Cert | Why | Notes |
|---|---|---|
| **CompTIA Network+** | Networking fundamentals everything else depends on | Skip if you already have a networking background |
| **CompTIA Security+** | Most widely recognized entry-level cert in the industry | Required or preferred by most employers; get this first |

### Phase 2: Specialization (once you've chosen a pillar)

| Pillar | Cert | Why It Matters |
|---|---|---|
| Offensive | **eJPT** | Affordable, hands-on, proves basic pentest ability |
| Offensive | **CompTIA PenTest+** | Broad vendor-neutral offensive foundation |
| Offensive | **OSCP** | Gold standard; 24-hour hands-on exam; highly respected |
| Defensive | **CompTIA CySA+** | Focused on threat detection and analysis |
| Defensive | **BTL1** | Affordable, practical, well-regarded for entry-level defensive work |
| Engineering | **AWS/Azure/GCP Security** | Choose the cloud your target employers use |
| Engineering | **CCSP** | Vendor-neutral cloud security; broadly respected |
| GRC | **CISM** | Most respected GRC cert; requires work experience |
| GRC | **CRISC** | Risk-focused; mid-career target |

### Phase 3: Senior Level

**CISSP** (Certified Information Systems Security Professional) covers eight domains of security knowledge and requires five years of work experience to hold. It's recognized everywhere and signals serious professional credibility. Pursue it after a few years of mid-level experience.

{% hint style="warning" %}
**Don't collect certifications as a substitute for skills.** A resume full of credentials and no demonstrable ability is easy to spot in an interview. The certifications should confirm capabilities you already have, not paper over gaps you haven't addressed.
{% endhint %}

---

## Don't Fall for the Expensive Cert Trap

The cybersecurity training industry is enormous and very good at making you feel like you need to spend thousands of dollars before anyone will hire you. You don't.

{% hint style="danger" %}
**Watch out for these specifically:**

- **SANS courses** -- Excellent content, $5,000 to $7,000 per course. Worth it later when an employer pays. Not where you start.
- **EC-Council CEH** -- ~$2,000, widely considered mediocre by working professionals. It's a multiple-choice exam testing memorized definitions. A solid TryHackMe profile impresses technical hiring managers more.
- **Bootcamp programs** -- $15,000 to $20,000 promising job-readiness in 12 weeks. Some are fine. Many are not. Research outcomes data, not marketing claims.
- **CISSP prep courses** -- $3,000 to $5,000. Largely unnecessary. The official ISC2 study guide plus practice exam platforms costs under $100.
{% endhint %}

The pattern is the same across all of them: vendors benefit when you believe credentials require expensive training. That's not always true.

What actually signals competence to hiring managers, especially technical ones: **a working project on GitHub**. Not an impressive-sounding project. A working one. Something you built, that runs, that solves a problem. One real project tells me more about a candidate than five vendor certifications.

If you don't have a GitHub profile yet, that's your first task after reading this.

---

## How Long Does This Actually Take?

{% hint style="info" %}
**Realistic timeline from zero technical background:**
- **6 to 12 months** of focused effort gets most people to their first entry-level job
- **3 to 6 months** if you already have a networking or IT background

The people who take longer usually spread attention across too many certifications at once, or study without building hands-on practice alongside the theory.
{% endhint %}

---

## Further Reading

| Resource | What it covers |
|---|---|
| [Professor Messer](https://www.professormesser.com) | Free, comprehensive video courses for Network+, Security+, CySA+. Widely regarded as best free study resource. |
| [CompTIA](https://www.comptia.org) | Official source for exam objectives, pricing, and approved study materials. Always check here before buying anything. |
| [Offensive Security (OSCP)](https://www.offsec.com) | Home of OSCP and Proving Grounds practice labs. |
| [OWASP Top 10](https://owasp.org/www-project-top-ten/) | Definitive reference for the ten most critical web application security risks. |
| [ISC2 CISSP](https://www.isc2.org/certifications/cissp) | Official CISSP exam content, experience requirements, and CBK domains. |
| [ISACA](https://www.isaca.org) | Home of CISM, CRISC, and CISA. Essential if GRC is your pillar. |

---

*Have questions, want feedback on your GitHub or LinkedIn, or just need a nudge in the right direction? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out directly on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). And if this book helped you, contribute back -- that commit on your GitHub is worth more than you think.*
