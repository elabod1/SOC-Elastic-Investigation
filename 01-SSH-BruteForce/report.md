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
3. Analysis
The activity is highly suspicious due to:

Automated Pattern: Fixed 21-second intervals indicate a script.

Successful Compromise: The 20th attempt succeeded, confirming the server was breached.

MITRE ATT&CK: T1110.001 (Brute Force), T1078 (Valid Accounts), T1021.004 (SSH).
4. Conclusion
True Positive – Successful SSH Brute Force compromise.

5. Recommendations
Block the source IP on the firewall.

Isolate the affected server.

Disable root SSH login (PermitRootLogin no).

Enforce SSH Key authentication and MFA.

Deploy Fail2Ban.

