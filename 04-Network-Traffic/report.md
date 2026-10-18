# 🛡️ Task 4: Network Traffic Investigation (C2)

## 1. Incident Summary
Multiple internal hosts, including the compromised `linux-app-01` and `win-admin-01`, were observed making repeated outbound connections to a single destination IP on port 443 (HTTPS), indicating Command and Control (C2) beaconing.

## 2. Evidence
- **Destination Port:** 443 (HTTPS)
- **Event Action:** connection_allowed
- **Affected Hosts:** linux-app-01, win-admin-01, linux-db-01, win-user-01, web-dmz-01
- **Total Connections:** 21
- **Correlation:** Connections occurred seconds after host compromise.

### KQL Query Used:
```kql
event.category: "network" and event.action: "connection_allowed" and destination.port: 443
```
3. Analysis
C2 Beaconing: Repeated connections to the same destination indicate a C2 channel.

Port 443 Abuse: Adversaries use HTTPS to blend with legitimate traffic.

Correlation: linux-app-01 connected 4 seconds after SSH compromise; win-admin-01 connected 22 seconds after PowerShell execution.

MITRE ATT&CK: T1071.001, T1573.002, T1041.

4. Conclusion
 True Positive – Active C2 communication confirmed.

5. Recommendations
Block the destination IP on the firewall.

Isolate all affected hosts.


Capture PCAP for forensic analysis.

Enable NetFlow/Packetbeat for network visibility.
