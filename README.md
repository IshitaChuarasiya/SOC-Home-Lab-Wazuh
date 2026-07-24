# SOC Home Lab using Wazuh and Sysmon

## Project Overview

This project documents my journey of building a SOC (Security Operations Center) Home Lab using Wazuh and Sysmon. The purpose of this lab is to understand how security events are collected, analyzed, and monitored in a real-world environment.

This repository contains my learning notes, lab setup, configurations, screenshots, and practical exercises completed while learning Wazuh.

---

## Objectives

- Learn the basics of Wazuh
- Set up a Wazuh Manager and Windows Agent
- Install and configure Sysmon
- Generate security events
- Analyze alerts in the Wazuh Dashboard
- Learn Regular Expressions (Regex)
- Create custom decoders

---

## Lab Environment

| Component | Details |
|-----------|---------|
| Host OS | Windows 10 |
| Virtualization | VirtualBox |
| Attacker Machine | Kali Linux |
| SIEM | Wazuh |
| Endpoint | Windows 10 |
| Monitoring Tool | Sysmon |

---

## Lab Architecture

```text
                    +----------------------+
                    |   Windows 10 Host    |
                    +----------+-----------+
                               |
                     Oracle VirtualBox
                               |
        +----------------------+----------------------+
        |                      |                      |
        |                      |                      |
+---------------+     +----------------+     +------------------+
| Wazuh OVA     |     | Windows 10 VM  |     | Kali Linux VM    |
|               |     |                |     |                  |
| Manager       |<----| Wazuh Agent    |     | Wazuh Agent      |
| Indexer       |     | Sysmon         |---->|                  |
| Dashboard     |<----------------------------- Logs -----------|
+---------------+
```

## Repository Structure

```text
docs/
images/
README.md
```

---

## Topics Covered

- Introduction to Wazuh
- Lab Setup
- Wazuh Installation
- Windows Agent Installation
- Sysmon Installation
- Generating Test Logs
- Alert Analysis
- Regex Basics
- Custom Decoders

---

## Future Improvements

As I continue learning Wazuh, I will update this repository with:

- Custom Rules
- MITRE ATT&CK Mapping
- Threat Hunting
- Active Response
- Sigma Rules
- Automation

---

## Acknowledgements

This repository is part of my cybersecurity learning journey and is continuously updated as I gain more practical experience.
