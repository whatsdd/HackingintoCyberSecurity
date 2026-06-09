# Home Lab and Portfolio

## Why This Chapter Exists

Two things get people hired in cybersecurity without prior experience: a place to practice safely, and proof they did. This chapter covers both. A **home lab** is an environment you control where breaking things is the point — no permission needed, no laws broken, no production to take down. A **portfolio** is the public record of what you learned there, the thing a hiring manager looks at before they read your resume carefully.

Earlier chapters mentioned both in passing. This one is the build guide. By the end you'll know how to set up a lab on any budget and how to turn what you do in it into evidence that gets interviews.

---

## The Core Idea: A Safe Place to Break Things

You cannot learn offensive or defensive security by reading. You learn it by attacking a vulnerable machine, watching the attack in the logs from the defender's side, breaking a configuration and fixing it, and doing that a few hundred times. Doing any of that against systems you don't own is a crime (Chapter 3). A home lab gives you legal targets and the ability to see both sides of every technique.

The good news, repeated throughout this book: this costs little or nothing. The barrier is not money. It's starting.

---

## Lab Tiers by Budget

Pick the tier that matches what you have *today*. You can always grow into the next one — and the $0 tier is enough to land a first job.

### Tier 0 — $0: The Browser and the Cloud

You need no hardware beyond the device you're reading this on.

- **In-browser platforms.** TryHackMe and Hack The Box run vulnerable machines and a Kali "attack box" entirely in your browser. You attack real targets without installing anything. This is the fastest possible start and covers months of learning.
- **Cloud free tiers.** AWS, Azure, and GCP offer free-tier accounts. You can stand up (and, critically, *secure* and *attack*) a real cloud environment — an over-permissive IAM role, a public storage bucket, a misconfigured security group — which is exactly the kind of thing breached in the real world. **Set a billing alert immediately**; a forgotten resource is the one way this tier costs money.

{% hint style="warning" %}
**The one rule of cloud labs: spend control.** Before you create anything, set a billing alert and a budget cap. The classic beginner mistake is leaving a resource running and getting a surprise bill. Tear down what you're not using.
{% endhint %}

### Tier 1 — A Laptop You Already Own: Local VMs

Once you want to keep machines around, build a virtual lab on your own computer.

- **Hypervisor:** [VirtualBox](https://www.virtualbox.org) is free, cross-platform, and more than enough to start. (VMware Workstation has a free personal-use tier too.)
- **What to run:** a Kali Linux VM as your attacker, plus one or more vulnerable targets (see the starter builds below).
- **Requirements:** 16 GB of RAM is comfortable for running two or three small VMs at once; 8 GB works if you run one target at a time. An SSD makes everything pleasant.
- **The habit that matters: snapshots.** Before you attack or modify a VM, take a snapshot. When you break it (you will), roll back in seconds instead of rebuilding for an hour. This single habit is what makes a local lab usable.

### Tier 2 — A Cheap Dedicated Box: A Real Lab

When you outgrow a laptop, a dedicated machine runs many VMs at once and stays on.

- **Hardware:** a used small-form-factor PC or mini-PC with 32 GB+ of RAM is the sweet spot, often available cheaply secondhand. You do not need a server rack.
- **Hypervisor:** [Proxmox VE](https://www.proxmox.com) is a free, type-1 hypervisor that turns that box into a proper virtualization host you manage from a browser — the same kind of skill cloud and infrastructure roles want.
- **What this unlocks:** a persistent multi-machine network — a Windows Active Directory domain, a Linux web server, a detection stack, and a Kali attacker, all running together so you can practice realistic, multi-step attacks and the detection of them.

---

## Networking Your Lab: Keep It Isolated

This is the part beginners get wrong, and it matters: **your vulnerable VMs must not be reachable from your real network or the internet.** You are intentionally running insecure machines; exposing them is how a learning lab becomes a foothold into your home.

The hypervisor networking modes you'll choose between:

| Mode | What It Does | Use For |
|---|---|---|
| **Host-only / Internal** | VMs talk to each other and the host, but **not** the internet | Vulnerable targets — the safe default for an attack lab |
| **NAT** | VMs reach the internet through the host, but aren't reachable from outside | A target that needs updates, or your Kali box for downloading tools |
| **Bridged** | VMs appear as real devices on your physical network | Rarely what you want for a security lab — it exposes vulnerable VMs to your LAN |

The standard safe pattern: put your attacker and vulnerable targets together on a **host-only/internal network** so they can see each other but nothing else can see them. Give Kali a second NAT adapter only when it needs to download tools. Never put a deliberately vulnerable machine on bridged networking.

{% hint style="danger" %}
**Common beginner mistakes, and the fixes:**
- *Bridged networking on a vulnerable VM* → use host-only/internal instead. A "Metasploitable" box on your home Wi-Fi is a real risk.
- *No snapshots* → snapshot before every experiment; rolling back is the whole point of VMs.
- *Running everything at once on too little RAM* → run one target at a time on a laptop; that's fine.
- *Forgotten cloud resources* → billing alerts and teardown discipline.
- *Treating the lab as disposable junk* → document it (see Portfolio below); the documentation is half the value.
{% endhint %}

---

## Starter Lab Builds by Pillar

Match your lab to the pillar you chose in Chapter 1. Each of these is free.

### Offensive / Attack Lab

The classic first lab: an attacker and a deliberately vulnerable target on an isolated network.

- **Attacker:** Kali Linux (free VM image from kali.org).
- **Targets:** start with [Metasploitable 2/3](https://github.com/rapid7/metasploitable3), [DVWA](https://github.com/digininja/DVWA), or [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/) for web. Then move to [VulnHub](https://www.vulnhub.com) machines (Mr-Robot, the Kioptrix series) for full-box compromises.
- **What you practice:** recon with Nmap, web exploitation with Burp, getting a shell, privilege escalation, and writing it all up.

### Defensive / Detection Lab

Build the attacker lab above, then add the defender's view so you can *see* attacks, not just launch them.

- **Detection stack:** [Security Onion](https://securityonionsolutions.com) (a free, all-in-one network monitoring and SIEM distribution) or a [Wazuh](https://wazuh.com)/Elastic stack.
- **Telemetry:** install Sysmon on a Windows target for rich endpoint logging.
- **What you practice:** run an attack from your Kali box, then hunt it in the logs — build a detection rule, watch it fire, tune out the false positives. This "attack then detect" loop is exactly SOC and detection-engineering work, and it's the most underrated lab a beginner can build.

### GRC "Lab": Artifacts, Not Machines

GRC doesn't need VMs — it needs documents that prove you can do the work. Build a portfolio of realistic artifacts for a fictional company:

- A risk register populated with real risks (use the NIST SP 800-30 template from Chapter 5).
- Two or three tailored security policies (start from the SANS templates in Chapter 4).
- A NIST CSF 2.0 gap assessment or an ISO 27001 Statement of Applicability (Chapters 4 and 5).
- A mock audit: pick a framework, map a fictional company's controls to it, and write up the gaps.

These artifacts *are* your lab and your portfolio at once. A hiring manager for a GRC role would rather see a competent mock risk assessment than any certification.

---

## The Portfolio: Turning Practice Into Proof

A home lab teaches you. A portfolio gets you hired. The two are the same activity recorded in public.

### Why It Works

Hiring managers, especially technical ones, check GitHub before they read a resume closely (Chapter 1). A portfolio answers the question certifications can't: *can this person actually do the work, and can they explain it?* It's also the way around the experience catch-22 — you generate evidence of skill without a job, by documenting what you do in your lab.

### What Goes In It

- **Writeups.** Every box you own, every CTF challenge you solve, every lab you build — write a clear technical walkthrough (Chapters 3 and 12). What you found, how you approached it, what failed first, how it could be fixed. A repo full of these is the single strongest entry-level signal.
- **Tools and scripts.** Small things you built to automate something tedious — a log parser, a recon script, a CVE checker. They don't need to be impressive. They need to *work* and have a clear README.
- **Lab documentation.** A writeup of your home lab itself: the architecture, the network design, what you run and why, with a diagram. This demonstrates you can build and explain infrastructure.
- **GRC artifacts** (for that pillar): the risk registers, policies, and assessments above.
- **Open-source contributions.** Even small ones. This book is open source — fixing or improving it is a real contribution you can point to (Chapter 1).

### How Hiring Managers Read It

What they're looking for, in order: *Does it exist? Does it work? Can they explain their thinking? Do they work consistently over time?* That last one is why a steady trickle of small writeups beats one big polished project dropped the week before applying. A green-ish contribution graph and a handful of clear writeups say "this person actually does this," which is the whole game.

{% hint style="success" %}
**Make your README do the work.** Most recruiters spend seconds on a repo. A clear top-level README — what this is, what you learned, a screenshot or diagram — turns a pile of files into a story. Pin your three best repos on your GitHub profile. Link the profile from your resume and LinkedIn.
{% endhint %}

### Common Portfolio Mistakes

- **Empty or private.** A private GitHub is invisible. Make your learning public (minus anything sensitive).
- **Overselling.** Don't claim a tutorial you followed as original work; interviewers probe, and Chapter 13's "never bluff" rule applies to portfolios too.
- **No explanation.** Code with no README and writeups with no reasoning don't demonstrate the thing employers want — your thinking.
- **Leaking secrets.** Don't commit API keys, your home IP, or anything from a real employer. Scan your own repos (Chapter 10's Gitleaks exercise).
- **Waiting for perfect.** Publish the rough version. Consistency and visibility beat polish.

---

## Try This

1. **Stand up a two-VM lab tonight.** Install VirtualBox, import a Kali image and a Metasploitable (or DVWA) target, and put both on a **host-only** network. Take a snapshot of each. Run `nmap -sV` from Kali against the target. You now have a legal, isolated place to practice everything in Chapters 2, 3, and 11.
2. **Write your first lab writeup.** Document the lab you just built: a diagram of the network, what each VM is, why it's isolated, and the first thing your Nmap scan found. Push it to a public GitHub repo with a clear README. That repo is the first entry in your portfolio.
3. **Pin your best work.** Create (or clean up) your GitHub profile, write a one-line bio that says what you do, and pin your three strongest repos. Link it from your LinkedIn and resume. Recruiters will find it — make the first impression count.

---

## Key Takeaways

- A home lab is a legal, isolated place to practice both attack and defense. It costs little to nothing — the barrier is starting, not money.
- Match the tier to what you have: in-browser and cloud free tiers ($0), local VMs on your laptop, or a cheap dedicated Proxmox box. The $0 tier is enough to get hired.
- Isolation is non-negotiable: keep vulnerable VMs on host-only/internal networking, never bridged, and snapshot before every experiment.
- Build the lab that fits your pillar — attack lab, attack-then-detect lab, or GRC artifacts — and watch both sides of every technique.
- The portfolio is the lab recorded in public. Writeups, working tools, lab documentation, and open-source contributions are the proof of skill that beats certifications and breaks the experience catch-22.
- Consistency and clarity win: small, frequent, well-explained work with good READMEs, pinned and linked, says "this person actually does this."

---

*Building a lab or a portfolio and want feedback on either? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back — improving this book is itself a portfolio piece.*
