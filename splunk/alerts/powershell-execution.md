# PowerShell Execution Detection

## Overview

This alert detects PowerShell execution activity on Windows endpoints using Sysmon process creation events.

---

# Detection Logic

The alert searches for PowerShell process execution events in Splunk telemetry.

## SPL Query

```spl
index=* powershell.exe
```

---

# Severity

Medium

---

# Why This Matters

PowerShell is commonly used by:

- System administrators
- Automation scripts
- Threat actors

Attackers frequently abuse PowerShell for:

- Malware execution
- Payload delivery
- Command execution
- Privilege escalation

---

# Alert Configuration

| Setting | Value |
|---|---|
| Alert Type | Scheduled |
| Schedule | Every 5 minutes |
| Time Range | Last 5 minutes |
| Trigger Condition | Number of Results > 0 |

---

# Validation Procedure

The alert was validated by manually executing PowerShell on the Windows 11 endpoint.

## Test Command

```powershell
powershell
```

---

# Expected Result

The alert should appear in:

- Splunk Triggered Alerts
- Splunk Search & Reporting

The detection should display:

- User account
- Process name
- Command line
- Host system

---

# Screenshots

## Triggered Alert

![Triggered Alert](../../screenshots/alerts/Win11%20Sysmon%20Triggered%20Alerts.png)

## Sysmon Alert Logs

![Sysmon Logs](../../screenshots/alerts/Windows11%20Sysmon%20Alerts.png)

---

# Skills Demonstrated

- Splunk alert creation
- Sysmon telemetry analysis
- SPL query development
- Behavioral detection engineering
- Windows process monitoring
