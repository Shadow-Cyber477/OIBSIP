# Task 5: Research Report — Social Engineering Attacks

## Introduction

**Social engineering** is hacking the person instead of the computer. Instead of breaking through a firewall, the attacker tricks someone into handing over access, like a thief who talks the guard into opening the door instead of picking the lock.

It is one of the most effective attack methods because it targets human traits (trust, fear, curiosity, helpfulness), and no software patch can fix those. The numbers show how big the problem is:

- The **2025 Verizon Data Breach Investigations Report** found that about **60% of breaches involved a human element**, such as a clicked phishing link, a manipulated employee, or misused credentials.
- The **FBI's 2025 Internet Crime Report** (published April 2026) recorded **$20.9 billion** in total reported losses. **Phishing/spoofing was the most reported crime type, with 191,561 complaints**, and **business email compromise (BEC)**, a form of impersonation fraud, caused about **$3.05 billion** in losses across 24,768 complaints.

This report covers the three main types (phishing, pretexting, baiting), plus quid pro quo as a bonus, with real case studies and practical defenses.

---

## 1. Phishing

### What It Is and How It Works
Phishing is a fake message that pretends to be from someone you trust (a bank, your boss, IT support) to trick you into clicking a link, opening a file, or giving up a password. The attacker uses urgency ("Your account will be locked in 1 hour!") so you act before you think.

### Types

| Type | How it works |
| :--- | :--- |
| **Phishing** | Mass emails sent to thousands of people, hoping a few respond. |
| **Spear phishing** | A message written for one specific person or team, using details about them (name, job, colleagues). |
| **Whaling** | Spear phishing aimed at senior executives (CEO, CFO) because they can approve big payments or access. |
| **Vishing** | Voice phishing: a phone call from a "bank" or "IT helpdesk". |
| **Smishing** | Phishing by SMS or messaging apps, often a fake delivery or bank alert with a link. |

### Real-World Case Study: Twitter Hack (July 2020)
Attackers phoned a small number of Twitter employees, pretending to be from the company's internal IT team, and tricked them into giving up their credentials. Twitter itself described this as a **"phone spear-phishing attack"**. Using those credentials to reach internal admin tools, the attackers targeted **130 accounts**, posted from **45**, viewed the private messages of **36**, and downloaded the data of **7**. The hijacked accounts belonged to well-known figures and companies and were used to post a Bitcoin "send me coins and I'll double them" scam that collected over **$100,000**. The alleged mastermind was a 17-year-old from Florida, who later accepted a three-year prison sentence.

**Lesson:** The attackers never "broke" Twitter's systems. They persuaded a few employees to open the door.

### Prevention Recommendations
1. **Use phishing-resistant multi-factor authentication (MFA).** Security keys or passkeys (FIDO2) stop a stolen password from being enough, because they only work on the real website.
2. **Filter and authenticate email.** Turn on spam/phishing filters and set up SPF, DKIM, and DMARC so attackers can't easily forge your company's domain.
3. **Verify unusual requests through a second channel.** If a message or call asks for money, passwords, or access, hang up and call back on a number you already know, or confirm in person.
4. **Make reporting easy and safe.** Add a "Report phishing" button, run regular phishing simulations, and thank people who report instead of blaming those who click.

---

## 2. Pretexting

### Definition
Pretexting is when an attacker invents a believable **story (the "pretext")** and a fake identity to make the victim willingly share information or take an action. It is less about a trick link and more about acting.

### How an Attacker Builds a False Scenario
1. **Research the target.** The attacker collects names, job titles, and company details from LinkedIn, company websites, and social media.
2. **Choose a believable identity.** Examples: IT support, a new employee, an auditor, a vendor, or the victim's own boss.
3. **Create a reason and pressure.** For example, "I'm from the bank's fraud team and we've spotted suspicious activity" or "The CEO needs this done before her flight."
4. **Make contact and build trust.** The attacker uses the collected details and confident language to sound real.
5. **Make the ask.** The victim shares a code, resets a password, sends records, or changes a payment detail. Many BEC scams work this way, with the attacker posing as an executive or supplier.

### Real-World Case Study: Hewlett-Packard (2006)
Concerned about leaks to the press, HP's board chairwoman authorized an investigation into the leaks. Investigators hired to run it obtained private phone records by **calling phone companies and posing as the account holders**, including HP board members and **nine journalists**. The scandal led to a U.S. House hearing in September 2006 and to the chairwoman stepping down from her role. Pretexting for phone records was a major reason the U.S. later passed a law against it.

**Lesson:** Pretexting works when an organization gives out information to anyone who *sounds* like they should have it.

### Prevention Measures
1. **Verify identity independently.** Never confirm sensitive details to an inbound caller. Call back using a number from an official source.
2. **Set strict verification rules for helpdesks and finance teams.** Password resets and payment-detail changes need a documented process (for example, a callback plus a second approver), no matter how senior the caller claims to be.
3. **Limit what attackers can learn.** Share less about staff and internal systems publicly, and train people that "I'm in a hurry, just this once" is a warning sign, not a reason to skip the rules.

---

## 3. Baiting

### Definition
Baiting offers something tempting, like a free item or download, to lure the victim into infecting themselves. It's the digital version of a fishing lure.

### Forms
- **Physical baiting:** Infected **USB drives** left in parking lots, lobbies, or mailed to targets, often labeled to look important ("Payroll," "Confidential").
- **Digital baiting:** **Fake downloads** such as cracked software, free movies or games, fake "PDF reader" updates, or ads promising free prizes, all carrying malware.

### Real-World Case Studies
**Study: University of Illinois USB drop (2016).** Researchers from the University of Illinois, the University of Michigan, and Google left **297 USB drives** around a campus. **About 48%** were plugged into a computer and had a file opened, the first within about **six minutes**. Most people took no security precautions, and many said they were just trying to find the owner. This shows how easily curiosity and kindness are exploited.

**Attack: FIN7 mailed USB drives (2020–2022).** The FBI warned that the criminal group FIN7 mailed packages to companies (retail, hospitality, then transportation, insurance, and defense) containing a USB drive with a fake letter, sometimes impersonating Amazon or the U.S. Department of Health and Human Services, and sometimes with a gift card. The USBs were "BadUSB" devices that pretend to be a keyboard, automatically type commands into the computer, and install malware, leading to ransomware.

### Prevention Measures
1. **Never plug in unknown devices.** Hand any found or mailed USB drive to the IT/security team.
2. **Control USB use with technology.** Disable autorun, block or restrict USB ports through endpoint policy, and allow only approved devices, since some malicious USB devices pose as keyboards.
3. **Download only from official sources.** Use company-approved software stores, web filtering, and application allow-listing, and keep antivirus/EDR updated.

---

## 4. Quid Pro Quo (Bonus)

### Explanation
*Quid pro quo* means "something for something". The attacker offers a **service or reward in exchange for information or access**. The typical example is a caller pretending to be from IT support who says, "I'll fix your slow computer, I just need your login," or who talks the victim into installing "support" software that gives the attacker remote control. Attackers often call many people until they find someone who actually has a problem, so the offer seems perfectly timed. Tech support scams alone accounted for about **$2.1 billion** in reported losses in the FBI's 2025 report.

### Prevention
- Use only the official IT support channel (ticket system or known number). Real IT staff will never ask for your password.
- Never install remote-access software because of an unexpected call.
- Treat any "free help" or "free gift in return for details" offer as suspicious, and report it to your security team.

---

## Comparison Table

| Attack Type | Primary Target | Psychological Lever Exploited | Best Countermeasure |
| :--- | :--- | :--- | :--- |
| **Phishing** | Any email, SMS, or phone user; spear/whale phishing target specific staff and executives | Urgency, fear, authority, greed | Phishing-resistant MFA plus a second-channel check of any unusual request |
| **Pretexting** | Helpdesks, finance and HR staff, customer-service agents, phone and utility companies | Trust and helpfulness, respect for authority | Strict identity verification and callback procedures |
| **Baiting** | Curious or busy employees; the general public | Curiosity and greed (the "free" item) | Never plug in or install unknown items; block USB and unapproved downloads |
| **Quid Pro Quo** | Employees and home users with a real or invented problem | Reciprocity, wanting help ("a favour for a favour") | Use official support channels only; never share credentials |

---

## Organisational Recommendations: 5-Point Employee Security Awareness Training Checklist

- [ ] **1. Teach the red flags.** Cover urgency, unexpected requests, mismatched sender addresses, unusual links, and offers that are too good to be true, with real examples like those in this report.
- [ ] **2. Run regular phishing simulations.** Do short, frequent exercises (not one annual session) and use the results to coach, not punish.
- [ ] **3. Set and practice a "verify before you trust" rule.** Require callback or second-person approval for payment changes, password resets, and data requests. Practice it in role-plays.
- [ ] **4. Enforce clear device and download policies.** Staff must never plug in found or mailed USB drives, and they must use only approved software sources.
- [ ] **5. Make reporting fast and blame-free.** Provide a one-click "Report" button and a clear contact for suspicious calls, messages, or devices, and reward people who report.

---

## References

1. **Verizon.** (2025). *2025 Data Breach Investigations Report*. Verizon Business. https://www.verizon.com/business/resources/reports/2025-dbir-data-breach-investigations-report.pdf
2. **Federal Bureau of Investigation, Internet Crime Complaint Center (IC3).** (2026). *2025 Internet Crime Report*. https://www.ic3.gov/AnnualReport/Reports/2025_IC3Report.pdf
3. **Tischer, M., Durumeric, Z., Foster, S., Duan, S., Mori, A., Bursztein, E., & Bailey, M.** (2016). *Users Really Do Plug in USB Drives They Find*. Proceedings of the 2016 IEEE Symposium on Security and Privacy. http://research.google.com/pubs/archive/45597.pdf
4. **U.S. House of Representatives, Committee on Energy and Commerce, Subcommittee on Oversight and Investigations.** (2006). *Hewlett-Packard's Pretexting Scandal* (Hearing, 109th Congress). U.S. Government Publishing Office. https://www.govinfo.gov/content/pkg/CHRG-109hhrg31472/html/CHRG-109hhrg31472.htm
5. **NPR.** (2020, July 31). *Florida Teen Charged As Mastermind Of Massive Twitter Hack*. https://www.npr.org/2020/07/31/897815039/florida-teen-charged-as-mastermind-of-massive-twitter-hack
6. **Dark Reading.** (2022). *FBI Warns FIN7 Campaign Delivers Ransomware via BadUSB*. https://www.darkreading.com/cyberattacks-data-breaches/fbi-warns-fin7-campaign-delivers-ransomware-via-badusb
