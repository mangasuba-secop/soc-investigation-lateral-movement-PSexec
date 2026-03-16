# soc-investigation-lateral-movement-PSexec
SOC investigation detecting lateral movement using PsExec and Windows event logs.
SOC Investigation — Lateral Movement Using PsExec
1. Incident Scenario

A SIEM alert detected suspicious login activity followed by remote command execution between two systems inside the network.

Initial indicators suggested possible lateral movement by an attacker.
Security logs Observed:
4624 — Successful login (user: lili)
4672 — Special privileges assigned
4688 — Process created: powershell.exe
4624 — Successful login to SERVER-01 from WS-102
4688 — Process created: psexec.exe
5140 — Network share accessed: \\SERVER-01\C$
       Investigation Process:
1: Identified suspicious successful login activity.
2: Observed privilege escalation throught Even ID 4672.
3: Detected execution of PsExec, a tool often used for remote command execution
4: Noticed access to administrative share C$ on SERVER-O1.
5: Correlated events indication lateral movement from WS-102 to SERVER-01
Initial Login → Privilege Escalation → PowerShell Execution → PsExec Execution → Server Access.

Findings
The investigation indicates that the compromised account was used to perform lateral movement within the network using PsExec, 
