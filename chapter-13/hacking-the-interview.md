# Hacking the Interview

## The Interview Is Also a System With Vulnerabilities

Every system has weaknesses. Hiring processes are systems. They have inputs (your resume, portfolio, conversations), processing logic (how interviewers evaluate candidates), and outputs (offer or rejection). They have assumptions that are often wrong and failure modes that skilled candidates can anticipate.

This chapter is about understanding that system well enough to navigate it effectively -- not to deceive, but to present genuine competence in the way that hiring processes are actually designed to detect it.

The cybersecurity job market is large, growing, and short of qualified candidates. If you have built real skills, the interview is mostly a communication challenge. If you have not built real skills yet, no interview advice will save you. This chapter assumes you have done the work.

---

## Before You Apply: The Prerequisites

Hiring managers in cybersecurity are often practitioners themselves. They can tell the difference between someone who has studied security and someone who has done it. Before applying for roles, verify you have the baseline:

{% hint style="success" %}
**Non-negotiable before applying for technical roles:**
- CompTIA Security+ (or equivalent demonstrated knowledge)
- A GitHub profile with at least one working project or documented lab
- Ability to discuss the OWASP Top 10 with concrete examples
- Comfortable in a Linux terminal (navigation, file management, process inspection)
- One hands-on platform completed: TryHackMe Jr Pentester path, HTB Starting Point, or equivalent

**Nice to have (significantly increases pass rate):**
- A solved CTF writeup or two published publicly
- A home lab you can describe and have documented
- One pillar-specific certification beyond Security+ (eJPT, BTL1, AWS Security)
- An open-source contribution you can point to
{% endhint %}

If you do not have the non-negotiables yet, stop reading this chapter and go build them. Come back in three months.

---

## The Resume

A cybersecurity resume has one job: get you a phone screen. It is not a comprehensive biography. It is a targeted document that signals relevant competence in the time an overloaded recruiter will give it.

**What interviewers actually look for:**

- Can this person do the specific job described in the JD?
- Do they have evidence of relevant skills (not just claims)?
- Is there something specific to ask about in an interview?

**Format:**

- One page for under 10 years of experience. Two pages maximum.
- No objective statement. Use that space for skills or projects.
- Reverse chronological. Current or most recent job first.
- PDF format. ATS-parseable (no tables, headers/footers, or text boxes).

**What to include:**

| Section | What to Put |
|---|---|
| **Contact** | Name, city (not full address), LinkedIn URL, GitHub URL, professional email |
| **Summary** (optional) | 2-3 sentences max; your current level, target role, and one differentiator |
| **Skills** | Specific tools and technologies: Splunk, Burp Suite, Python, Nmap, AWS, not "teamwork" |
| **Experience** | Quantified accomplishments, not job descriptions. "Reduced alert volume by 30% by tuning SIEM rules" not "Responsible for SIEM monitoring" |
| **Projects** | Home lab, CTF achievements, open-source contributions, anything you built |
| **Certifications** | Name, issuer, year. No expiration dates that have passed. |
| **Education** | Degree + year. Relevant coursework only if recent graduate with thin experience. |

{% hint style="warning" %}
**Things that hurt your resume:**
- "Proficient in Microsoft Office" (not relevant)
- Listing every certification you have ever heard of (dilutes credibility)
- Spelling or grammar errors (signals lack of attention to detail in a field where details matter)
- Generic bullet points that could apply to any security job ("Worked as part of a team to solve problems")
- A Gmail address with a name like `hackerman1337@` (use firstname.lastname@)
{% endhint %}

---

## Tailoring Applications

Sending the same resume to 200 jobs is less effective than sending a tailored resume to 20. Read the job description carefully. Mirror its language in your resume where truthful. If the JD says "threat hunting" and you have threat hunting experience described as "proactive threat detection," update the language.

Look at the required vs. preferred qualifications. Required qualifications are genuine gates. If you meet 70%+ of preferred qualifications, apply. Many job descriptions are wish lists written by hiring managers who know they will not find a perfect candidate.

Research the company before applying:
- What industry are they in? (Healthcare, finance, defense each have specific compliance contexts)
- Do they have a published security team? (LinkedIn, conference talks, GitHub)
- Have they had a notable breach? (Reading post-mortems tells you what they care about)
- What is the glassdoor review of the security team?

---

## The Phone Screen

Most processes start with a 30-minute recruiter phone screen. Recruiters are evaluating basic fit and communication -- not technical depth.

**What recruiters assess:**
- Can this person communicate clearly?
- Do they understand what role they're applying for?
- Are their salary expectations in range?
- Do they have the credentials and experience the job requires?

**Prepare for:**
- "Tell me about yourself" -- 90 seconds, focused on your security background and what you're targeting
- "Why are you interested in this role / company?" -- have a specific answer that is not "good pay"
- "What is your target salary?" -- research ranges on levels.fyi, Glassdoor, LinkedIn Salary. Give a range anchored at the top of what you consider fair.
- "Do you have [specific cert / tool experience]?" -- be honest; do not claim certifications you do not have

---

## The Technical Interview

Technical interviews in cybersecurity fall into three types, often combined:

### Type 1: Knowledge Questions

These assess whether you understand the fundamentals. Common topics by role:

**For SOC / Defensive roles:**
- What is the difference between IDS and IPS?
- Walk me through what happens when you receive a phishing alert
- How does DNS work? What is DNS poisoning?
- Explain the CIA triad and give an example of a control for each
- What is a SIEM? How do you tune detection rules to reduce false positives?
- What does the MITRE ATT&CK framework describe?

**For Penetration Testing / Offensive roles:**
- Walk me through a web application penetration test methodology
- What is SQL injection and how do you test for it?
- Explain the difference between XSS and CSRF
- What happens during a TCP three-way handshake?
- What is privilege escalation and what are common vectors on Linux? On Windows?
- If you have a shell on a box, what are the first things you do?

**For GRC / Compliance roles:**
- What is GDPR and what are the key obligations?
- Explain the difference between a vulnerability assessment and a penetration test
- What is risk appetite and how is it defined?
- How does ISO 27001 differ from SOC 2?
- What is the purpose of a BIA (Business Impact Analysis)?

{% hint style="info" %}
**How to answer knowledge questions you do not know:**

Be honest. "I haven't worked with that specific tool, but I'm familiar with the concept -- in [tool you do know], I've done X which is similar." Interviewers respect honesty and can tell when someone is bluffing. What they cannot tell immediately is whether you will learn quickly. Showing intellectual honesty and a learning mindset compensates for gaps.

Never claim knowledge you do not have. Security engineers are good at probing -- one follow-up question exposes a bluff immediately.
{% endhint %}

### Type 2: Scenario / Situational Questions

These present a realistic situation and ask what you would do. They test practical judgment, not just memorized answers.

**Common scenarios:**

*"A user reports their machine is acting strangely -- what do you do?"*

Structure your answer: Triage (isolate, preserve), Investigate (what are the indicators? logs, processes, network connections), Escalate (who needs to know?), Remediate (based on findings).

*"You discover during a pentest that the client has unpatched critical vulnerabilities on internet-facing systems that are out of scope. What do you do?"*

Report it immediately to the client's point of contact even though it is out of scope. Document that you did so. Do not exploit it. The client's safety takes precedence over scope definitions.

*"You receive an alert that an employee is exfiltrating data. The employee is the CFO. What do you do?"*

Escalate immediately to your manager and legal counsel. Do not confront the CFO directly. Preserve evidence without alerting the subject. Follow the incident response procedure.

The structure for scenario answers: **Situation assessment → Immediate action → Communication → Escalation → Documentation**. Every scenario response should touch all five.

### Type 3: Practical / Hands-On Challenges

Increasingly common for technical roles. You may be asked to:

- Analyze a PCAP file and identify malicious traffic
- Look at a piece of code and identify security vulnerabilities
- Perform a basic web application test on a provided target
- Complete a CTF-style challenge during the interview
- Review a security architecture diagram and identify weaknesses

**Preparation:**

Practice narrating while you work. Interviewers in practical assessments are evaluating your methodology as much as your result. Talking through what you are looking for and why you are trying each approach demonstrates experience in a way that correct answers alone cannot.

If you get stuck: state what you would do next if you had more time, what additional information you would want, and what your hypothesis is. An incomplete answer with good methodology often scores higher than a correct answer with no articulated reasoning.

---

## Questions to Ask

The questions you ask reveal as much as the answers you give. Always ask questions. Having no questions signals either disinterest or poor preparation.

**Questions that signal genuine engagement:**

- "What does the team's threat modeling process look like right now?"
- "How are security incidents handled -- what's the escalation process?"
- "What does success look like in this role in the first 90 days?"
- "What is the security team's relationship with the engineering team?"
- "What are the biggest security challenges the organization is facing right now?"
- "What does the on-call rotation look like, if any?"
- "How does the security budget get determined and how is it defended?"

**Questions about growth:**
- "What does professional development look like -- training, conference attendance, certifications?"
- "What have people in this role typically moved into?"

**Avoid:**
- "What is the salary?" (save for the offer stage unless they ask first)
- Questions answered on the company's public website (signals no preparation)
- "Is this a good place to work?" (too vague; ask a more specific version)

---

## Negotiating the Offer

Most candidates do not negotiate. Most candidates leave money on the table.

**Rules:**

1. **Never accept on the spot.** "Thank you so much -- I'm very excited about this. Can I have until [specific date, usually 3-5 business days] to review?" This is normal. Every recruiter expects it.

2. **Research the range first.** Use levels.fyi, Glassdoor, LinkedIn Salary, Glassdoor, and peers in similar roles to know what the market pays for this role in this geography.

3. **Negotiate salary, not just base.** The full package includes base salary, bonus target, equity (at tech companies), signing bonus, PTO, training budget, remote work policy, and equipment. Each is potentially negotiable.

4. **Make the counter specific.** "Based on my research and the skills I bring, I was expecting something closer to $X. Is there flexibility there?" is better than "Can you do better?"

5. **Let them respond.** After your counter, stop talking. Silence is uncomfortable. Resist filling it.

6. **Know your walk-away number.** Before the conversation, decide the minimum offer you would accept. Do not accept below it. Do not bluff if you would accept the original offer.

---

## The 30-60-90 Day Plan

Accepting an offer is not the end of the process. The first 90 days determine whether you are seen as a high performer who advances or someone who struggles.

**First 30 days:**
- Understand the environment: what systems exist, what the security architecture looks like, who the key stakeholders are
- Meet everyone on the team and adjacent teams (engineering, IT, legal, compliance)
- Read all existing documentation: policies, procedures, architecture diagrams, past incident reports
- Avoid changing anything major; listen and observe

**Days 31-60:**
- Identify gaps: what is missing, what is broken, what is generating the most pain
- Propose specific improvements with clear rationale
- Take ownership of one defined area or project
- Begin demonstrating reliability: deadlines met, communication clear, follow-through consistent

**Days 61-90:**
- Deliver a measurable result
- Have a direct conversation with your manager about expectations and how you are tracking
- Establish your working rhythm: what you own, how you report, what decisions you make independently

---

## Handling Rejection

You will be rejected. Many times, probably. The best practitioners in the industry have rejection stories.

What rejection tells you:

- Sometimes: you are not ready yet. Get the feedback and build what is missing.
- Sometimes: the role was not what it appeared to be, and you were right not to fit it.
- Sometimes: the decision was arbitrary, influenced by budget, internal candidates, or factors you could not have known.

What to do: ask for feedback specifically. Some will give it, many will not. Send a brief thank-you email regardless. Ask if they would keep you in mind for future openings. Keep the relationship intact.

One no is not the market's verdict on your career. It is one company's decision on one day. Update your approach based on patterns (if you consistently fail technical screens, build more technical depth; if you consistently fail to get to technical screens, improve your resume or networking), and keep going.

---

## References

[1] Cabaj, K., Domingos, D., Kotulski, Z., & Respicio, A. (2018). Cybersecurity education: Evolution of the discipline and analysis of master programs. *Computers & Security*, 75, 24--35. doi:10.1016/j.cose.2018.01.015

[2] Payscale. (2024). *Cybersecurity salaries: By role and experience*. PayScale. Retrieved from https://www.payscale.com/research/US/Skill=Information_Security/Salary

[3] LinkedIn. (2024). *Jobs on the Rise: Cybersecurity*. LinkedIn Economic Graph. Retrieved from https://www.linkedin.com/pulse/

[4] Glassdoor. (2024). *Information Security Analyst Salaries*. Glassdoor. Retrieved from https://www.glassdoor.com

[5] ISACA. (2023). *State of Cybersecurity 2023: Global Update on Workforce Efforts, Resources and Cyberoperations*. ISACA. Retrieved from https://www.isaca.org/resources/reports

---

## Further Reading

| Resource | What It Covers |
|---|---|
| [levels.fyi](https://www.levels.fyi) | Crowdsourced compensation data for tech and security roles at major companies |
| [Glassdoor Interview Questions](https://www.glassdoor.com/Interview/) | Real interview questions submitted by candidates at specific companies |
| [STAR Method](https://www.themuse.com/advice/star-interview-method) | Structured approach to answering behavioral interview questions |
| [Cracking the Cybersecurity Interview](https://github.com/nickapic/Cybersecurity-Interview-Preparation) | Community-curated list of common interview questions by role |
| Daniel Miessler's Blog (danielmiessler.com) | Career advice for security practitioners; honest, direct, practical |

---

*Preparing for an interview? Want a mock technical screen or resume feedback? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back -- this book is open source and your additions are welcome.*
