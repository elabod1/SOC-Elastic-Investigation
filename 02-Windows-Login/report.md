# 🛡️ Task 2: Windows Login Investigation

## 1. Incident Summary
A Brute Force attack targeted the `administrator` account on `win-admin-01`. After 12 failed attempts (Event ID 4625) with a ~10.8-second interval, a successful login (Event ID 4624) occurred.

## 2. Evidence
- **Target Host:** win-admin-01
- **Target Account:** administrator
- **Event IDs:** 4625 (Failed), 4624 (Success)
- **Failed Attempts:** 12
- **Successful Logins:** 1
- **Interval:** ~10.8 seconds

### KQL Query Used:
```kql
event.category: "authentication" and event.code: "4625"
