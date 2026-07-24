# Lab Setup

## Objective

The objective of this lab is to build a beginner-friendly Security Operations Center (SOC) environment for learning Wazuh and Sysmon.

---

## Lab Architecture

The lab environment consists of three virtual machines running in Oracle VirtualBox.

| Machine | Purpose |
|---------|---------|
| Wazuh v4.14.6 OVA | Wazuh Manager, Indexer, and Dashboard |
| Kali Linux | Security testing machine with Wazuh Agent |
| Windows 10 Lab | Endpoint monitored using Wazuh Agent and Sysmon |

---

## Virtualization

The lab environment is hosted using **VirtualBox**.

---

## Environment Overview

- Host Operating System: Windows 10
- Virtualization Software: Oracle VirtualBox
- Wazuh Version: 4.14.6
- Windows Endpoint: Windows 10
- Linux Endpoint: Kali Linux
- Log Monitoring: Sysmon + Wazuh Agent

## Software Used

| Software | Purpose |
|----------|---------|
| Wazuh | Security monitoring platform |
| Sysmon | Windows event logging |
| VirtualBox | Virtualization software |
| Kali Linux | Security testing |
| Windows 10 | Endpoint machine |

---

## Learning Goals

- Understand the Wazuh architecture
- Connect a Windows endpoint to Wazuh
- Monitor security events
- Generate alerts
- Learn Regex
- Build custom decoders

---

## Notes

This lab is intended for learning purposes and will be updated as I continue learning more Wazuh features.
