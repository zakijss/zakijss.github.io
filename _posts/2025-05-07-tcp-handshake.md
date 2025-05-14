---
title: "Analyzing a TCP Three-Way Handshake in Wireshark"
date: 2025-05-07
categories: [Portfolio, Wireshark]
tags: [tcp, wireshark, packets, networking, project, portfolio]
description: Capturing and analyzing a full TCP handshake using Wireshark.
toc: false
comments: false
media_subpath: /assets/img/
---

![Wireshark TCP Handshake](Wireshark-SYN.png){: w="700" h="400" }
_A captured SYN → SYN-ACK → ACK sequence completing a TCP connection._

As part of a demonstration in network analysis, I captured a TCP three-way handshake using Wireshark. This is the process by which two devices establish a reliable connection over TCP.

---

### Summary of the Handshake

| Packet # | Type     | Description                            |
|----------|----------|----------------------------------------|
| 1        | SYN      | Client initiates connection            |
| 2        | SYN-ACK  | Server acknowledges and replies        |
| 3        | ACK      | Client acknowledges, connection ready  |

**Destination IP:** 142.250.1.139 (example Google server)  
**Port Used:** 80 (HTTP)

---

### Critical Observations

- This is a **classic handshake pattern**:
  - The client sends a **SYN** packet to begin the connection.
  - The server replies with a **SYN-ACK**.
  - The client responds with an **ACK**, completing the handshake.
- No data is exchanged during the handshake itself, it’s strictly for session setup.
- This specific capture was tied to a connection attempt on port 80 (HTTP).

---

### Use Case

Being able to recognize and interpret a TCP handshake is crucial for:

- **Detecting anomalies** (e.g., incomplete handshakes, SYN floods)
- **Troubleshooting failed connections**
- **Understanding how connections are initiated before attacks occur**

This capture helped me reinforce how baseline connection behavior looks at the packet level, it is a skill that feeds directly into incident analysis, IDS tuning, and traffic filtering.
