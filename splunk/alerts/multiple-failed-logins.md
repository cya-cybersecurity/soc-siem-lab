
# Multiple Failed Login Detection

## Overview

This alert detects repeated failed Windows login attempts using Windows Security Event logs ingested into Splunk Enterprise.

The detection is designed to identify potential brute-force attacks or repeated authentication failures.

---

# Detection Logic

The alert searches for Windows failed login events and counts repeated occurrences by host.

## SPL Query

```spl
index=* 4625
| stats count by host
| where count > 5
```

---

# Severity

Medium

---

# Why This Matters

Repeated failed login attempts may indicate:

- Brute-force attacks
- Password spraying
- Unauthorized access attempts
- Misconfigured services
- User authentication issues

Monitoring failed authentication activity is a core SOC analyst responsibility.

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

The alert was validated by intentionally entering incorrect Windows login credentials multiple times on the Windows 11 endpoint.

## Test Procedure

1. Locked the Windows 11 system
2. Entered incorrect password more than 5 times
3. Generated Windows Event ID 4625 failed login events

---

# Expected Result

The alert should generate a triggered alert inside Splunk and display:

- Failed login counts
- Host system
- Authentication failure events
- Timestamps

---

# Skills Demonstrated

- Splunk alert creation
- Authentication monitoring
- Windows Security Event analysis
- SPL statistical aggregation
- Detection engineering
- Brute-force detection concepts
