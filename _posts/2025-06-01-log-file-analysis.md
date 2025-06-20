---
title: "Log File Analyzer for Suspicious Activity Detection"
date: 2025-06-01 
categories: [Portfolio, Logs]
tags: [python, log analysis, threat detection, portfolio, project]
description: A Python script that reads log files, detects suspicious patterns such as failed logins and access violations, and reports potential threats for security analysis.
layout: post
---

So this project is a Python-based log file analyzer designed to identify and report suspicious activity from common system and web server logs. It targets patterns that indicate potential security incidents such as brute-force login attempts, port scans, and unauthorized access to restricted resources.

The goal was to simulate the early-stage detection workflows typically performed by Security Operations Center (SOC) analysts or system administrators by automating initial log triage, so it can be expanded upon and useful in that sense.

## Purpose

Analyzing logs manually can be tedious and error-prone. This tool automates detection logic to accelerate initial investigations and reduce the cognitive load on analysts. It is particularly useful for small environments or as a starting point for building a custom Security Information and Event Management (SIEM) system.

## Features

- Supports .log file input from services like OpenSSH (auth.log) or Apache/Nginx (access.log)
- Identifies failed login attempts, repeated access from the same IPs, port scan behavior, and probing of restricted URLs
- Aggregates and formats output for easy review
- Includes modular regex detection engine for extending or refining signatures
- CLI-based interface for integration with other tools or cron jobs

## Technical Implementation

The analyzer is implemented in Python 3. It reads a log file line by line and applies a set of regex-based detection rules. Each rule is associated with a threat type and a severity level.

Detection rules are defined in a separate dictionary.

Matched events are stored with timestamp, IP address (if available), and rule type. Results are printed to the console and optionally written to an output file.

## Example Output

```
[2025-06-01 21:31:44] WARNING - Repeated failed SSH login from 192.168.1.45
[2025-06-01 21:32:05] INFO    - Possible port scan detected from 103.21.244.0
[2025-06-01 21:34:09] ALERT   - Attempted access to /admin (403 Forbidden) from 45.67.89.123
```

## Usage

```bash
python log_analyzer.py --input /path/to/file.log --output report.txt
```

Command-line arguments used are:

* `--input` to specify the log file
* `--output` to write results to a report file
* `--verbose` to include contextual lines around the match

## Potential Extensions

* Add GeoIP resolution for flagged IPs
* Integrate with blocklists or auto-blacklist IPs using a firewall
* Create a simple web interface for report visualization
* Incorporate basic machine learning models for anomaly detection

## Skills Demonstrated

* Regular expression engineering for security detection
* Parsing and normalizing logs across different formats
* Building CLI tools with argparse
* Basic automation for incident triage and alerting
* Writing clean, extensible Python code for operational security

This tool highlights hands-on cybersecurity and automation skills relevant to log forensics, threat hunting, and system monitoring workflows. It provides a strong foundation for expanding into real-time detection, reporting, or SIEM integration.
