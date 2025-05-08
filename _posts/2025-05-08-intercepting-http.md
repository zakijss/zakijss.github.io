---
title: "Intercepting HTTP Login Credentials with Wireshark"
date: 2025-05-08
categories: [Portfolio, Wireshark]
tags: [http, wireshark, cleartext, network-analysis, networking, packets, project, portfolio]
description: Capturing and analyzing HTTP POST traffic containing unencrypted credentials.
toc: false
comments: false
media_subpath: /assets/img/
---

![Wireshark HTTP POST Credential Capture](Insecure-HTTP.png){: w="700" h="400" }
_A captured POST request over HTTP showing clear-text credentials._

In this project, I used Wireshark to capture traffic from my browser and identified login credentials being transmitted in clear text over an insecure HTTP connection.

---

###  How It Was Done

1. Started a Wireshark capture on Wi-Fi.
2. Visited `http://neverssl.com` to trigger unencrypted HTTP traffic.
3. Used the filter `http.request.method == "POST"` to isolate form submissions.
4. Located the POST request containing form data in plain text.

---

### Observations Made:

The captured packet showed:

- `POST /login` in the Info column
- HTTP headers and form fields visible
- `username=C3A43231426` and `pass=HMAC%7Bnj5jy6wzgykyj4e7e6swjag9gge%3D%7D` included in the body

This proves that anyone intercepting this traffic could easily retrieve sensitive credentials if the site doesn't use HTTPS.

---

### Key Takeaway

This exercise highlights the risks of sending data over HTTP. In real-world scenarios, attackers could:
- Use packet sniffers on public Wi-Fi
- Capture credentials during form submissions
- Launch MITM attacks if HTTPS is not enforced

Modern sites must use HTTPS with proper TLS encryption to prevent this kind of data exposure.
