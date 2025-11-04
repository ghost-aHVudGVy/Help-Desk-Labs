# Remote Access & Support Tools Lab

This lab focused on configuring and testing different remote access tools within a Windows domain environment. The objective was to simulate how IT support professionals remotely manage systems, assist users, and maintain secure connectivity between domain computers.

The main goal was to enable and verify **Remote Desktop Protocol (RDP)**, simulate a remote support session, and document the process as it would be done in a real IT environment.

## Overview

By the start of this lab, the following environment was already set up and running:

| Component | Hostname | Role | IP Address | Description |
|------------|-----------|------|-------------|--------------|
| **DC01** | `DC01` | Domain Controller | 192.168.10.10 | Active Directory Domain Services, DNS, DHCP |
| **Client01** | `Client01` | Workstation | DHCP | Domain-joined Windows 10 client |
| **Internal Network** | `LabNet` | Virtual Network | 192.168.10.0/24 | Isolated internal network used for domain communication |

This setup replicates a small corporate environment, with both machines connected through an isolated internal network to simulate a real enterprise domain.

---

## Step 1 – Enabling and Testing Remote Desktop (RDP)

I began by enabling **Remote Desktop** on both the domain controller (DC01) and the client machine (Client01).  
This allowed secure, administrative-level access for remote management within the domain.

After enabling RDP through **Settings → System → Remote Desktop**, I confirmed that the feature was properly configured by allowing it through the Windows Firewall using PowerShell:

```powershell
Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
```
Next, I verified that the Remote Desktop Services were running:
```powershell
Get-Service TermService
```
Once the service status showed as “Running,” I initiated a connection from DC01 to Client01 using the built-in Remote Desktop Connection tool (mstsc).
The connection was successful, confirming that remote administration within the domain was functioning correctly.

**Screenshots:**
- [RDP-Enabled](./screenshots/01_RDP-Enabled.png)
- [Allow-RDP-In-The-Firewall](./screenshots/02_Allow-RDP-In-The-Firewall.png)
- [Successful-RDP-Connection](./screenshots/03_Successful-RDP-Connection.png)

This step demonstrated my ability to configure and verify RDP access — a core skill in server and workstation management.

## Step 2 – Simulating a Support Session Log

To make the lab more realistic, I documented a simulated IT support scenario.
I created a support log (SupportSessionLog.txt) to reflect how remote troubleshooting sessions are recorded in professional environments.

Example log entry:
```
Session ID: RDP-001
Tool: Remote Desktop
Date: 2025-11-03
Technician: A.K.
Client: Client01
Issue: Group Policy not updating
Action Taken: Forced GPUpdate and restarted Windows Update service
Outcome: Resolved successfully
```

This simple step demonstrates not just technical execution, but also attention to documentation
Logs are very important accountability, traceability, and clarity during support operations.

## Outcome
By the end of the lab, I had successfully:

- Configured and verified Remote Desktop (RDP) for remote management.
- Created a structured support session log to simulate real-world IT documentation.
- Confirmed secure connectivity and functional communication between the domain controller and the client system.

Although this lab primarily focused on RDP, it laid the groundwork for additional remote access methods such as TeamViewer and Quick Assist, which follow the same verification and documentation process.
