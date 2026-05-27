
# New Account Creation Detection

## Overview

This alert detects new Windows user account creation activity using Windows Security Event logs forwarded into Splunk Enterprise.

Unauthorized account creation can indicate persistence, privilege escalation, or unauthorized administrative activity.

---

# Detection Logic

The detection searches for Windows Event ID 4720 account creation events.

## SPL Query

```spl
index=* EventCode=4720
| table _time host Account_Name SubjectUserName
```

---

# Severity

High

---

# Why This Matters

Threat actors may create new accounts to:

- Maintain persistence
- Escalate privileges
- Establish unauthorized access
- Evade account lockouts
- Create backup administrative accounts

Monitoring account creation activity is critical for security visibility and incident response.

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

The alert was validated by creating a test user account on the Windows 11 endpoint.

## Test Command

```cmd
net user testadmin Password123! /add
```

---

# Expected Result

The alert should generate a triggered alert inside Splunk and display:

- New account name
- User that created the account
- Host system
- Timestamp

---

# Skills Demonstrated

- Splunk alert creation
- Windows Security Event monitoring
- Account management monitoring
- Detection engineering
- Endpoint telemetry analysis
- Security operations workflow
