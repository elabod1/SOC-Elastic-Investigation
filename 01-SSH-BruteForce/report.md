# 🛡️ Task 1: SSH Brute Force Investigation

## 1. Incident Summary
A coordinated SSH Brute Force attack was detected against `linux-app-01`. After 19 failed attempts with a consistent 21-second interval, a successful login occurred, indicating a confirmed compromise.

## 2. Evidence
- **Target Host:** linux-app-01
- **Source IP:** (Sanitized)
- **Failed Attempts:** 19
- **Successful Logins:** 1
- **Time Window:** ~7 minutes
- **Interval:** 21 seconds (automated pattern)

### KQL Query Used:
```kql
event.category: "authentication" and event.outcome: "failure" and event.action: "ssh_login"
