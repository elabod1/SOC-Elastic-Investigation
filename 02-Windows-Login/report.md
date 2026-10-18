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
```
3. Analysis
Automated Pattern: Fixed interval indicates a script (e.g., Hydra/Crowbar).

High-Value Target: administrator is the highest privileged account.

Compromise Confirmed: The successful 4624 event confirms the account was breached.

MITRE ATT&CK: T1110.001, T1078.002.

4. Conclusion
 True Positive – Successful compromise of the Windows Administrator account.

5. Recommendations
Isolate the host and disable the administrator account.

Enforce Account Lockout Policy.

Enable MFA on RDP.

Restrict RDP to VPN only.

