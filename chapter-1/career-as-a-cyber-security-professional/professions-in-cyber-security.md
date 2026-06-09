# Getting the Job

Everything in the previous sections was preparation. This section is about execution: finding the right roles, researching employers intelligently, avoiding common mistakes, and having an honest picture of what the career is actually like once you're in it.

---

## The Honest Pros and Cons

Before you invest months building toward this career, you deserve a straight answer on what it's actually like.

{% hint style="success" %}
**Why cybersecurity is a genuinely great career:**
- The work is never boring. The threat landscape evolves constantly, and you will never run out of things to learn.
- Job security is strong once you're in: experienced practitioners stay in demand even through tech downturns. (Honesty requires saying: the *entry* level has gotten more competitive since 2023 — which is exactly why the proof-of-work approach in this book matters.)
- Salaries are strong at every level: entry-level pays significantly better than comparable roles in most other fields
- Remote work is standard: the majority of roles are fully remote or hybrid
- You can self-train your way in: TryHackMe, Hack The Box, free courses, and CTFs mean you can build demonstrable skills without a $50,000 degree
{% endhint %}

{% hint style="warning" %}
**What they don't tell you upfront:**
- **Alert fatigue is real.** If you start in a SOC, you will spend a lot of time chasing false positives. This is the part that doesn't make it into career brochures.
- **The stakes create pressure.** When a breach happens, the impact is real. Some people thrive under that weight. Others burn out. Be honest with yourself.
- **Staying current is a continuous commitment.** A few years of coasting will erode your skills in this field.
- **Not all companies take security seriously.** You'll encounter organizations that treat security as a compliance checkbox. Choosing where you work matters enormously.
- **On-call is part of many roles.** Attacks don't respect business hours.
{% endhint %}

---

## Finding the Right Roles

**Where to look**

| Platform | Best For |
|---|---|
| LinkedIn | Most useful single platform; recruiters actively search here |
| Indeed / Glassdoor | Broad searches; use Glassdoor reviews before interviewing |
| [CyberSeek](https://www.cyberseek.org) | US-specific job demand by region and role |
| USAJOBS | US government and defense contractor roles |
| HackerOne / Bugcrowd / Intigriti | Bug bounty; consistent findings are evidence of offensive skill |

**What to look for in an employer**

The company's security maturity matters more than the job title. A company with a well-funded, respected security team in a culture that treats security as a business priority is worth taking a slightly lower salary for, especially early in your career.

{% hint style="info" %}
**Questions worth asking in interviews:**
- What does the security team's relationship with engineering look like?
- How are security incidents handled and reviewed?
- What does the team's learning and development budget look like?
- How long do most people in this role stay before advancing?

If the interviewer can't answer these clearly, that itself is information.
{% endhint %}

---

## Do You Even LinkedIn?

Seriously. Go look at your LinkedIn profile right now.

Is the headline generic ("Aspiring Cybersecurity Professional" tells me nothing)? Is the summary empty, or does it read like a form letter? Have you posted anything in the last six months? Do you have any connections in the field?

LinkedIn is not optional in this industry. It is where recruiters actively search for candidates, where hiring managers check you out after your resume lands, and where your professional network lives. A weak or empty profile is a missed opportunity every single day.

{% hint style="info" %}
**What a strong cybersecurity LinkedIn looks like:**
- Headline that says what you do *specifically*: "SOC Analyst | CompTIA Security+ | TryHackMe Top 10%" beats "Aspiring Cybersecurity Professional" every time
- Summary in plain human language: where you're coming from and where you're going
- Certifications listed
- Some sign of activity: sharing an article, commenting in the community, posting about a lab you completed

You don't need to be a content creator. You need to exist and look like someone who gives a damn.
{% endhint %}

---

## Your GitHub Is Your Real Resume

When I'm hiring, I check GitHub before I read the resume carefully. So do most technical hiring managers I know.

{% hint style="success" %}
**What matters on GitHub:** Working projects. Not impressive ones. *Working* ones.
- A Python script that scrapes CVE data
- A home lab write-up documented in a repo
- A small tool you wrote to automate something tedious
- A CTF writeup repo where you document your thinking

None of this needs to be polished. It needs to exist and show effort.
{% endhint %}

If your GitHub is empty or private, that's your most important task before you send another job application.

And if you don't know where to start with open source: you're reading an open-source book right now. This book lives on GitHub. Fixing a typo, improving a section, adding a resource you found useful is a real open-source contribution. You can put it on your CV. It counts.

---

## The AI-Era Job Hunt

Hiring changed. Your application is now read by software before any human sees it, and your interviewer assumes you have an LLM open in another tab. Work with that reality instead of pretending it away.

**Getting past the machines.** Most companies run applications through an ATS, increasingly with AI-assisted ranking. This means: mirror the exact phrasing of the job posting for skills you genuinely have ("incident response", not "handling security events"), keep formatting simple (no columns, tables, or graphics in the resume file), and tailor every application. Tailoring is fifteen minutes with an LLM: paste the posting and your resume, ask which requirements you're not clearly demonstrating, then fix the gaps *truthfully*. Don't let the model invent experience — interviewers are very good at finding the bullet you can't back up.

**Using AI to prepare — the legitimate edge.** The best free interview prep available is an LLM with a good prompt: "You are a SOC manager interviewing a junior analyst. Ask me one question at a time, push back on weak answers." Do this for an hour and you'll hear your own gaps. Same for negotiating: rehearse the salary conversation against an AI playing a tough recruiter.

**Where the line is.** Covertly using AI *during* a live technical screen is a fast way to get rejected — interviewers notice the cadence, and many companies state policies up front. If a take-home assignment doesn't specify, ask. Using AI openly and well ("I'd draft the query with an assistant, then verify it because LLMs get SPL syntax wrong") routinely impresses interviewers; hiding it never does. Expect at least one interview question about how you use AI tools — have a real answer with a real example.

---

## Show Up. Physically, If You Can.

Most people wait to feel ready before showing up anywhere. That's backwards.

Security conferences and meetups are where the industry actually lives:
- **OWASP chapter meetings.** Free, most major cities.
- **BSides events.** Community-organized, low-cost or free, highly accessible.
- **DEF CON and Black Hat.** Student discounts available.
- **Local ISACA and ISC2 chapters.** Often discounted or free for students and unemployed members.

{% hint style="info" %}
**Just ask.** Many events offer discounted or free tickets for recent grads or first-time attendees. The worst they can say is no. Showing up matters more to most organizers than the ticket price.
{% endhint %}

What you do when you get there: talk to people. Not to network in the transactional sense, but because these are people who do the work you want to do. Ask what they're working on. Ask what they wish they'd learned earlier. Most practitioners in this community are generous with their time. The conversations you have at a BSides event will do more for your trajectory than many hours of solo studying.

---

## Internships and Training Positions: Don't Be Proud

A paid internship at a well-known company, or an unpaid one if you can afford it, is one of the fastest paths into a full-time role. The name on your resume matters less than you'd think for landing jobs later. The experience and the reference matter enormously.

Sitting and waiting for the perfect opportunity is the worst thing you can do. An imperfect role you took, learned from, and turned into a reference is worth far more than the ideal role you're still hoping to get.

Training positions, apprenticeships, even junior helpdesk roles at companies with security teams are all entry points. Many of the best security professionals started somewhere unglamorous. The job you take isn't the job you stay in. It's the job you use to get to the next one.

---

## On Discrimination

It happens. Most people in positions to discriminate won't admit it, even to themselves. You may face it because of your name, your background, your accent, your gender, your age. It is real and it is wrong and you will not always be able to prove it.

{% hint style="warning" %}
**The honest truth:** Focus on what you can control. The hiring manager who discriminates against you is often the same person who needs help desperately and can't find it. Keep building your skills. Keep showing up. Keep making your work visible. The volume of genuine, quality attempts eventually beats inaction every time.

The industry is facing a massive talent shortage. Good practitioners who can demonstrate real skill will find employers who want them. Not every employer. But enough.
{% endhint %}

Don't let one bad interview, one silent rejection, or one frustrating experience stop forward motion. The data is on your side. Keep going.

---

## One More Thing About This Book

How much of this did you actually read? Be honest.

The authors of this book, and the contributors who've helped build it, share decades of combined experience here for free. No paywall. No upsell. No course to buy afterward.

The point is: you don't need to buy a fancy program, book, or course to get into this field. The information exists. Much of it is free. The bottleneck is never access to information. It's doing the work.

If this book helped you, the best thing you can do is contribute back. Fix something that's wrong. Add a resource. Improve a section. Submit a pull request on GitHub. Your name goes in the contributor list, and you have a legitimate open-source contribution to put on your resume. That matters to hiring managers who know what to look for.

Don't know how to contribute to open source yet? This is your first project.

---

## Your 30-Day Launch Plan

You don't need to be ready to start. You need to start to get ready.

### Week 1: Build Your Foundation

- Create a free account on **TryHackMe**. Complete the "Pre-Security" learning path (~10 hours: networking basics, Linux, and how web technology works)
- Install **VirtualBox** (free) and set up a Linux VM (Ubuntu is a good choice). Spend time every day in the terminal: navigation, file management, process management, piping commands
- Watch **Professor Messer's CompTIA Network+** series on YouTube for free. Take notes in your own words

### Week 2: Go Hands-On

- Complete TryHackMe's **"Introduction to Cybersecurity"** path, which covers how attacks work, what defenders do, and gives you a taste of each pillar
- Set up **DVWA** (Damn Vulnerable Web Application) on your Linux VM. Practice every OWASP Top 10 vulnerability in this safe environment. Document what you learn
- Based on what you've experienced this week, **commit to one of the four pillars**, not forever, just for now

### Week 3: Build a Visible Presence

- Create a **LinkedIn profile** specifically for your cybersecurity journey. Document what you're learning and what certifications you're pursuing
- Join the **TryHackMe Discord**, r/cybersecurity, or a relevant professional community
- Find **three professionals** on LinkedIn doing the work you want to do in five years. Study their career paths

### Week 4: Make a Commitment

- **Register for CompTIA Security+.** You don't need to be ready yet. You need a deadline. 60 to 90 days from now is reasonable. Having money on the line focuses the studying.
- Identify your **primary practice platform** and use it daily
- Write a simple **one-page plan**: your target pillar, your first certification, and the job title you want 12 months from now

{% hint style="success" %}
**Twelve months is achievable.** People do it regularly. The timeline depends entirely on consistency and quality of practice, not just hours logged. Forty focused hours beats two hundred passive ones. Find a community of people at a similar stage. The cybersecurity practitioner community is unusually open and helpful.
{% endhint %}

---

## Beyond 30 Days: The 12-Month Roadmap

The 30-day plan gets you moving. Here's the rest of the year, assuming roughly 10–15 focused hours a week. Adjust the pace to your life, not the other way around — consistency beats intensity.

### Months 2–3 (everyone): Foundation and First Certification

- Pass **Security+** (Professor Messer's free videos + practice exams). This is the deadline you set in Week 4 — honor it.
- Keep daily terminal time. By month 3 you should be writing small Bash and Python scripts without copying them.
- Start a **learning log**: one short writeup per week of something you broke, built, or finally understood — in a GitHub repo. This becomes your portfolio and your interview material.

### Months 4–12 (by pillar)

| Months | Offensive | Defensive | Engineering | GRC |
|---|---|---|---|---|
| **4–6** | TryHackMe Jr Penetration Tester path; first 10 HTB boxes; sit **eJPT** | TryHackMe SOC Level 1 path; build a small detection home lab; start **CySA+ or BTL1** prep | Pick one cloud (AWS/Azure); its fundamentals cert; deploy and harden a small project on it | Read NIST CSF 2.0 and ISO 27001 Annex A controls; write a mock risk register and two policies for an imaginary company |
| **7–9** | PortSwigger Web Security Academy (all apprentice + practitioner labs); regular CTFs; bug bounty recon on easy programs | Pass CySA+/BTL1; learn one SIEM hands-on (Splunk free / Elastic); write detection rules for 5 ATT&CK techniques | Cloud security cert (e.g. AWS Security Specialty prep); learn Terraform basics; automate one security control end to end | Map a mock company to SOC 2 controls; study **CISA or CRISC** material; volunteer for any audit-adjacent task at your current job |
| **10–12** | **PNPT or OSCP prep** (only if fundamentals are solid — don't rush it); polish 3 best writeups; apply broadly | Build an end-to-end incident writeup (detection → containment → lessons); apply to SOC roles from month 9 onward | Publish your infrastructure project with documentation; apply to junior security/cloud engineer roles | Get one cert scheduled; turn your mock GRC artifacts into a portfolio repo; apply to analyst roles from month 9 onward |

Three notes on this table. First, **start applying around month 9, not month 12** — the job search itself takes months, interviews are training, and you can keep studying while you apply. Second, every path ends with a **portfolio, not just a cert** — that's deliberate, and it's what separates you from the other two hundred applicants with Security+. Third, if you're employed in IT already, compress this: your existing experience replaces months 2–3, and internal transfers into security teams are the most underrated entry path in the industry.

---

## Key Takeaways

- The honest trade-offs: strong pay, remote-friendly work, and real intellectual challenge — against alert fatigue, on-call, breach pressure, and a continuous learning obligation that never ends.
- LinkedIn and GitHub are not optional. A specific headline and three working projects beat a polished resume with nothing behind it.
- Hiring is AI-mediated now: tailor honestly for the ATS, use LLMs hard for preparation, and never use them covertly in live interviews.
- Show up where the industry lives — BSides, OWASP chapters, local meetups. Conversations beat cold applications.
- Follow the 12-month roadmap, start applying at month 9, and treat rejections as data. Consistency wins this game.

---

## Further Reading

| Resource | What it covers |
|---|---|
| [CyberSeek Career Pathway](https://www.cyberseek.org/pathway.html) | Interactive map of career transitions, certs per role, and job opening counts |
| Glassdoor Company Reviews | Read reviews from current/former security team members specifically |
| LinkedIn Salary Insights | Self-reported salary ranges by job title and location |
| [PicoCTF](https://picoctf.org) | Beginner CTF platform by Carnegie Mellon. Problems permanently available. |
| r/cybersecurity and r/netsec | Active communities; r/cybersecurity is career-focused, r/netsec is more technical |
| *Cybersecurity Career Master Plan* by Dr. Gerald Auger | Practical, experience-based guide written by someone who hired security professionals |

---

*Want someone to look at your LinkedIn or GitHub and give you honest feedback? Stuck on where to start? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/) -- happy to help. And if this book was useful to you, pay it forward: contribute to it, share it, or just send someone else here who needs it.*
