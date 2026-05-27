
# Encoded PowerShell Detection

## Overview

This alert detects encoded PowerShell execution activity on Windows endpoints using Sysmon process creation telemetry forwarded into Splunk Enterprise.

Encoded PowerShell commands are commonly used by attackers to obfuscate malicious activity and evade detection.

---

# Detection Logic

The detection searches for PowerShell commands using the `-enc` argument.

## SPL Query

```spl
index=* "-enc"
```

---

# Severity

High

---

# Why This Matters

Threat actors frequently abuse encoded PowerShell commands for:

- Malware execution
- Payload obfuscation
- Command-and-control activity
- Phishing payload delivery
- Defense evasion

Encoded PowerShell activity is considered suspicious because legitimate administrative usage is relatively uncommon in most environments.

---

# Alert Configuration

| Setting | Value |
|---|---|
| Alert Type | Scheduled |
| Schedule | Every 5 minutes |
| Time Range | Last 5 minutes |
| Trigger Condition | Number of Results > 0 |
| Trigger Action | Add to Triggered Alerts |

---

# Validation Procedure

The alert was validated by manually executing an encoded PowerShell command on the Windows 11 endpoint.

## Test Command

```powershell
powershell -enc ZQBjAGgAbwAgAHQAZQBzAHQA
```

---

# Expected Result

The alert should generate a triggered alert inside Splunk and display:

- PowerShell process execution
- Encoded command-line arguments
- User account
- Host system
- Timestamp

---

# Skills Demonstrated

- Splunk alert creation
- SPL query development
- Sysmon telemetry analysis
- Behavioral detection engineering
- PowerShell threat detection
- Windows endpoint monitoring
