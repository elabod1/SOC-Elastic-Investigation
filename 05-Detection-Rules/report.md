# 🛡️ Task 5: Detection Rule Creation

## 1. Incident Summary
Based on the investigations, 3 automated Detection Rules were created in Elastic Security to detect the attack chain: Brute Force, Account Compromise, and C2 Communication.

## 2. Evidence (Rules Created)

### Rule 1: Brute Force Authentication
- **Type:** Threshold
- **Severity:** High
- **Query:** `event.category: "authentication" and event.outcome: "failure"`
- **Group by:** `source.ip`
- **Threshold:** 5 attempts / 5 minutes

### Rule 2: Successful Login After Multiple Failures
- **Type:** Custom Query
- **Severity:** Critical
- **Query:** `event.category: "authentication" and event.outcome: "success" and source.ip: (IOC_IPs)`

### Rule 3: Suspicious Repeated Outbound Connections (C2)
- **Type:** Threshold
- **Severity:** Critical
- **Query:** `event.category: "network" and event.action: "connection_allowed" and destination.port: 443`
- **Group by:** `source.ip`, `destination.ip`
- **Threshold:** 3 connections / 10 minutes

## 3. Analysis
The rules cover the entire Kill Chain:
1. **Initial Access:** Rule 1 detects Brute Force early.
2. **Compromise:** Rule 2 alerts on the actual breach.
3. **Command & Control:** Rule 3 detects post-exploitation C2 traffic.

## 4. Conclusion
 **True Positive** – 3 Active rules deployed and tested.

## 5. Recommendations
- Enable Alert Notifications (Email/Slack).
- Create Runbooks for each rule.
- Conduct regular MITRE ATT&CK coverage reviews.
