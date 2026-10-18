# 🛡️ Task 3: Suspicious PowerShell Investigation

## 1. Incident Summary
24 seconds after the Windows Administrator account was compromised, a suspicious PowerShell command was executed on `win-admin-01` using obfuscation and execution policy bypass flags.

## 2. Evidence
- **Host:** win-admin-01
- **User:** administrator
- **Event Code:** 4688 (Process Creation)
- **Process:** `powershell.exe`
- **Command Line:** `powershell.exe -NoProfile -ExecutionPolicy Bypass -EncodedCommand <SIMULATED>`

### KQL Query Used:
```kql
event.category: "process" and process.name: "powershell.exe"
```
3. Analysis
Obfuscation: -EncodedCommand hides the true intent (Base64).

Defense Evasion: -ExecutionPolicy Bypass and -NoProfile bypass security controls.

Context: Execution immediately after compromise confirms malicious intent.

MITRE ATT&CK: T1059.001 (PowerShell), T1027 (Obfuscation), T1562.001 (Impair Defenses).

4. Conclusion
 True Positive – Malicious PowerShell execution confirmed.

5. Recommendations
Isolate the host immediately.

Enable PowerShell Script Block Logging (Event ID 4104).

Enable Constrained Language Mode.

Enable AMSI.
