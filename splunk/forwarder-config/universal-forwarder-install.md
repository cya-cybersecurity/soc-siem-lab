# Splunk Universal Forwarder Configuration

## Overview

This document outlines the installation and configuration of the Splunk Universal Forwarder on the Windows 11 endpoint used in the home SOC/SIEM lab.

The Universal Forwarder was configured to send Windows event logs and Sysmon telemetry to Splunk Enterprise running on Ubuntu Server.

---

# Components

| Component | Purpose |
|---|---|
| Splunk Universal Forwarder | Sends logs to Splunk |
| Windows 11 | Endpoint telemetry source |
| Sysmon | Endpoint monitoring |

---

# Installation Steps

## Download Universal Forwarder

Downloaded the Splunk Universal Forwarder from the official Splunk website.

## Install Universal Forwarder

Installed the Universal Forwarder on the Windows 11 VM.

---

# Configure Receiving Indexer

Configured the forwarder to send logs to the Splunk Enterprise server.

## Example

```text
192.168.1.10:9997
```

---

# Configured Log Sources

The following logs were forwarded:

- Sysmon Operational Logs
- Windows Security Logs
- Windows Application Logs

---

# Example inputs.conf Configuration

```ini
[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = 0
renderXml = true
index = main

[WinEventLog://Security]
disabled = 0
index = main
```

---

# Verification

Verified successful ingestion by confirming Windows logs appeared in Splunk Search & Reporting.

---

# Skills Demonstrated

- Splunk log ingestion
- Windows telemetry collection
- Forwarder configuration
- Sysmon integration
- SIEM data onboarding
