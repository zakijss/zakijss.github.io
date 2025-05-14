---
title: "File Integrity Verification with Hashing using CertUtil"
date: 2025-05-12
categories: [Portfolio, Cryptography]
tags: [hashing, certutil, integrity, sha256, security+, project, portfolio,]
description: Generating and comparing file hashes to verify data integrity on Windows 11 LTSC IoT.
toc: true
comments: false
media_subpath: /assets/img/
---

![CertUtil Hash Algorithm](hash-verified.png){: w="700" h="400" }
_Initial SHA256 hash generation using CertUtil._

To demonstrate integrity checking using cryptographic hashes, I used **CertUtil**, a built-in Windows utility, to generate and verify SHA256 hashes on local files. This technique is vital in areas like **forensics**, **secure backups**, and **malware detection**, where detecting unauthorized changes is critical.

---

### Test Setup

![CertUtil Testfile Creation](testfile.png){: w="700" h="400" }
_testfile successfully created and placed._

I created a sample file named `testfile.txt`, inserted simple text, and then used `CertUtil` to generate its hash. Afterwards, I modified the file to simulate tampering, then restored it to demonstrate hash matching.

After creating the sample file, i made a copy, so that it can be tampered with:

![Testfile Copy completed](copy-created.png){: w="700" h="400" }
_Copy of testfile.txt._

Then i tested the hashes:

![SHA256 Hashes tested](hash-identical.png){: w="700" h="400" }
_Identical SHA256 hash generation proven._

Afterwards, i _tampered_ with the copied file, and tested the hashes again:

![CertUtil Hash Tamper](hash-change-verified.png){: w="700" h="400" }
_Initial SHA256 hash is now different._

I also tested SHA1 and SHA512.

![Different Hash Expansion](hash-identical.png){: w="700" h="400" }
_Different hash algorithm visible._

This project ties directly into the Security+ Domain regarding Cryptographic Concepts.

Now, i have **successfully demonstrated** how:

__Hashes detect changes in files.__

__Cryptographic integrity checks are critical for verifying file authenticity.__

__SHA256 is a secure hashing algorithm supported by Windows natively via certutil.__

### Skills demonstrated:

**SHA256 hashing**

**Detecting file integrity violations**

**Using native Windows tools for secure file validation**

**Incident response preparation (malware detection, file baselining)**


---