---
title: "Blocking SMB Traffic via Windows Firewall: Reducing Lateral Movement Risk"
date: 2025-05-08
categories: [Portfolio, Host Security]
tags: [firewall, security+, smb, architecture, port-control, project]
description: Analyzing default firewall exposure and implementing host-based rules to block unnecessary and risky services like SMB.
toc: true
comments: false
media_subpath: /assets/img/
---

![Firewall Rule - Block Port 445](firewall-rule.png){: w="700" h="400" }
_Custom rule blocking inbound SMB traffic (port 445) applied to all network profiles._

This project demonstrates a key host-hardening tactic: blocking SMB (Server Message Block) traffic using **Windows Firewall with Advanced Security**. SMB, used for file sharing and printer services, is frequently abused in **lateral movement**, **worm propagation**, and **remote code execution** attacks, most notoriously in **WannaCry**, **EternalBlue**, and **NotPetya** campaigns.

---

### Why Port 445 Is a Risk?

| Threat Type         | Description                                             |
|---------------------|---------------------------------------------------------|
| Wormable exploits   | Port 445 is the primary vector for EternalBlue & WannaCry |
| Lateral movement    | Attackers use SMB to move between machines in a domain |
| Remote execution    | Unpatched SMB services can allow unauthenticated access |
| Enumeration vector  | SMB reveals shares, system names, and users to attackers |

Even if not externally accessible, internal exposure is risky in a compromised network.

---

### Steps Taken:

#### 1. Opened Windows Firewall Console
Via `wf.msc`, I launched **Windows Defender Firewall with Advanced Security**.

#### 2. Reviewed Existing Rules
Navigated to **Inbound Rules**, sorted by port. I found:

- **File and Printer Sharing (SMB-In)** enabled by default on Private networks
- Allowed inbound traffic to **TCP 445**, **UDP 137/138** — all part of SMB/NBNS stack

#### 3. Created a Custom Inbound Block Rule


![Firewall Properties - Block Port 445](firewall-properties.png){: w="700" h="400" }
_Custom rule blocking inbound SMB traffic (port 445) properties assessed correctly._

- **Rule Type**: Port  
- **Protocol**: TCP  
- **Port**: 445  
- **Action**: Block the connection  
- **Profile**: All (Domain, Private, Public)  
- **Name**: `Block SMB TCP 445 - Harden Host`  

The rule was placed above the existing allow rules for full effect.

---

### Verification & Testing

To validate the firewall was working:

- I attempted to access the host via nmap and other tools.

![Firewall Confirmation - Block Port 445](firewall-confirmed.png){: w="700" h="400" }
_Custom rule blocking inbound SMB traffic (port 445) confirmed._
