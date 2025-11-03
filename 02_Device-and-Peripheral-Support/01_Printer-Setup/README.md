# Print Server Deployment Lab (Virtual Printer via Group Policy)

This project demonstrates how I configured and managed a **Windows Print Server** in a domain environment — from installation to automated deployment using **Group Policy (GPO)**.  

The goal was to simulate a realistic enterprise setup where network printers are managed centrally through a print server, even without access to physical hardware. To achieve that, I created a **virtual printer** using a simulated IP address and deployed it to client machines within the domain.

---

## Overview

By the end of this lab, I had the following environment configured and fully functional:

| Component | Hostname | Role | IP Address | Description |
|------------|-----------|------|-------------|--------------|
| **DC01** | `DC01` | Domain Controller & Print Server | 192.168.10.10 | Handles AD DS, GPOs, and Printer Management |
| **Client01** | `Client01` | Domain-joined Workstation | DHCP | Used to test deployment and functionality |
| **Office_Printer** | Virtual Printer | Shared Resource | 192.168.10.200 (simulated) | Shared “Generic / Text Only” printer |

This project helped me strengthen my understanding of **print management, GPO deployment, and service troubleshooting** in Windows Server.

---

## Step 1 — Installing the Print Server Role

I began by installing the **Print and Document Services** role on my domain controller (DC01).  
Through **Server Manager → Add Roles and Features**, I selected the **Print Server** role service and completed the installation.

[Instal-Print-Role](/screenshots/01_Instal-Print-Role.png)

[Instaling-Print-Server](/screenshots/02_Instaling-Print-Server.png)

Once installed, I verified the **Print Spooler** service was running and enabled **File and Printer Sharing** through Windows Firewall.  
This ensured that the print server could communicate properly with client systems across the network.

[Print-Managemant-Tree](/screenshots/03_Print-Managemant-Tree.png)

[Spooler-Status.png](/screenshots/04_Spooler-Status.png)

[Enable-File-&-Printer-Sharing-(Firewall)](/screenshots/05_Enable-File-&-Printer-Sharing-(Firewall).png)

---

## Step 2 — Creating a Virtual Printer

Since there was no physical printer in the lab, I created a virtual one using a **Standard TCP/IP Port** with a simulated address: `192.168.10.200`.  

From the **Print Management Console**, I added a new printer:
- **Type:** TCP/IP Device  
- **Driver:** Generic / Text Only  
- **Printer Name:** Office_Printer  
- **Share Name:** Office_Printer

[AddPrinter-TCPIP](/screenshots/06_AddPrinter-TCPIP.png)
[Printer-Driver-Select](/screenshots/07_Printer-Driver-Select.png)
[Printer-Setup](/screenshots/08_Printer-Setup.png)
[Printer-Shared-Properties](/screenshots/09_Printer-Shared-Properties.png)


After installation, I confirmed that the printer appeared under `Print Management → DC01 → Printers` and that it was shared properly.  
This simulated setup allowed me to test print services exactly as they would work in a real network.

---

## Step 3 — Connecting from a Client (Manual Test)

Before deploying via Group Policy, I tested manual access from a domain workstation (`Client01`).  

Using File Explorer, I navigated to `\\DC01` and double-clicked on the shared **Office_Printer**.  
Windows automatically installed the driver and added the printer to the client’s device list.  

This confirmed that:
- Network connectivity was working correctly.  
- Printer sharing permissions were properly configured.  
- The driver installation succeeded without errors.

---

## Step 4 — Deploying the Printer via Group Policy

To make deployment automatic, I configured a **Group Policy Object** to distribute the printer to all domain users.  

From **Print Management**, I right-clicked the printer and selected **Deploy with Group Policy**.  
I created a new GPO named `GPO_Deploy_Printer`, linked it to the appropriate OU, and chose **Per User** deployment. 

[Deploy-Printer-via-GPO](/screenshots/11_PrintMgmt_DeployGPO.png)

After refreshing Group Policy on `Client01` (`gpupdate /force`), the printer appeared automatically under **Devices and Printers**, confirming successful GPO deployment.

[Client-Printer-Listings](/screenshots/12_Client-Printer-Listings.png)

---

## Step 5 — Verification and Testing

To validate the configuration, I performed a simulated print test:
- Opened **Printer Properties** on `Client01`
- Selected **Print Test Page**

[Test-Page-Print](/screenshots/13_Test-Page.png)

The print job completed successfully and cleared from the queue, showing that the entire communication chain — from client to print server — was functioning properly.

On the server side, I monitored the **Print Queue** in the Print Management console to confirm that the job passed through DC01 and was processed without errors.

[Server-Printer-Queue-Empty](/screenshots/14_Server-Printer-Queue-Empty.png)

---

## Step 6 — Troubleshooting and Validation

During setup, I ran through common troubleshooting steps to confirm service health and simulate real-world support scenarios:

- Checked the **Print Spooler** service using PowerShell:
  ```powershell
  Get-Service Spooler
- Verified firewall rules for File and Printer Sharing:
  - Get-NetFirewallRule -DisplayGroup "File and Printer Sharing"
- Confirmed driver and permissions from Printer Properties → Security tab.
- Used `Test-Connection` to verify reachability between DC01 and Client01.

These tests helped ensure the environment was stable and resilient — an important habit in enterprise IT work.

## Step 7 — Final Outcome

At the end of this lab:

- The print server role was installed and configured correctly.
- The virtual printer was shared and functional.
- Clients could connect manually or automatically through Group Policy.
- All permissions, services, and network settings were verified and working as expected.

This setup fully simulated how printers are deployed and managed in real Windows domain environments — from creation to user access.

## Conclusion

Completing this lab helped me gain hands-on experience with:

- Managing Print Services in Windows Server
- Deploying shared resources using Group Policy
- Troubleshooting spooler and driver issues
- Automating printer availability for end users

It also reinforced the importance of structured testing and documentation — key skills for systems administrators and IT support professionals.
