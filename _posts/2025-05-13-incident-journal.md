---
title: "Final Incident Handler’s Journal: A Security Entry"
date: 2025-05-13 
categories: [Portfolio, Journal]
tags: [incident-response, nist, tools, journaling, blue-team, portfolio, data entry,]
description: This is a comprehensive Incident Handling Journal list of entries, growing with time.
pin: true
toc: true
---

Throughout my cybersecurity learning experience, I’ve maintained an **Incident Handler’s Journal** to document key incidents, tools, and reflections. This post shares my finalized yet unfinished entries, which form part of my professional portfolio. It demonstrates both my analytical process and hands-on practice using core tools aligned with the **NIST Incident Response Lifecycle**, as well as other frameworks.

---

## Journal Entry 001 – Phishing Investigation

**Date:** 2025-05-14  
**Entry:** 001  
**Description:** Investigated and documented a phishing email incident using the 5 W's. This entry falls under the *Detection and Analysis* and *Containment* phases of the NIST IR Lifecycle.  
**Tool(s) used:** Outlook, VirusTotal  

**The 5 W's:**
- **Who:** External attacker impersonating HR  
- **What:** A phishing email with a fake benefits link  
- **When:** 2025-04-21 at 08:43 AM  
- **Where:** Sent to a company-wide employee mailing list  
- **Why:** Attempt to harvest employee credentials via a spoofed login page  

**Notes:**  
VirusTotal flagged the link. Credentials were reset, the domain was blocked, and a phishing simulation was scheduled. Clear communication and quick user reporting helped minimize damage.

---

##Journal Entry 002 – Suricata Rule & Malware Detection

**Date:** 2025-05-02  
**Entry:** 002  
**Description:** Wrote a Suricata rule to identify suspicious outbound traffic. Activity aligns with *Detection and Analysis*.  
**Tool(s) used:** Suricata, Wireshark  

**The 5 W's:**
- **Who:** Internal host infected with malware  
- **What:** Outbound traffic to a known malicious IP  
- **When:** 2025-05-01  
- **Where:** Internal subnet 192.168.1.x  
- **Why:** Attempted command-and-control (C2) communication  

**Notes:**  
Created custom rules to flag behavior. Wireshark confirmed the traffic. Host was isolated and cleaned. Reinforced the value of deep packet inspection and custom detection logic.

---

## Journal Entry 003 – Splunk Query & Dashboarding

**Date:** 2025-04-18  
**Entry:** 003  
**Description:** Practiced querying brute-force login attempts in Splunk. This falls under *Detection and Analysis*.  
**Tool(s) used:** Splunk  

**Tool Usage Summary:**
- Queried failed login events by `src_ip` and `user`
- Used visualizations to track patterns over time
- Set up alerting for excessive failures  
- Built dashboard for easy monitoring  

**Notes:**  
Splunk made correlation and alerting intuitive. This activity improved my ability to transform logs into actionable insights for security operations.

---

## Journal Entry 004 – File Hash Investigation

**Date:** 2025-04-10  
**Entry:** 004  
**Description:** Investigated a SHA256 file hash and analyzed sandbox results. Aligns with *Detection and Analysis*.  
**Tool(s) used:** VirusTotal, Any.run, Hybrid Analysis  

**Tool Usage Summary:**
- VirusTotal: hash flagged by 39 vendors  
- Any.run: revealed ransomware-like behavior  
- Hybrid Analysis: tracked file behavior and external calls  

**Notes:**  
This investigation showed how tools complement each other. Multi-source validation helped form a clear risk assessment of the file. Learned how to enrich indicators of compromise (IOCs).

---

## Final Reflections

This journal represents my hands-on learning in a structured, repeatable format. Tracking the **NIST IR Lifecycle** helped me understand each phase of incident response, from identifying issues to responding and learning from them.

Here’s what I gained:
- Confidence using tools like **Suricata**, **Splunk**, **Wireshark, **Nmap**, and **VirusTotal**
- Skill in writing detection rules and queries
- Habit of documenting investigations clearly
- Understanding of how to isolate threats, identify attackers, and respond systematically  

I’ll keep building on this journal in my career every now and then and refer to it as both a record of learning and a portfolio piece.

---

_Thanks for reading everyone! If you'd like to see more practical incident response case studies, stay tuned for future posts or connect with me on LinkedIn._

