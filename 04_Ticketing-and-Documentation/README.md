# Ticketing System & Knowledge Base Lab

This repository showcases my hands-on experience simulating a professional IT Help Desk environment. The project focuses on managing support requests using **Jira Service Management** alongside a Windows domain lab, documenting solutions in Knowledge Base (KB) articles, and demonstrating real-world troubleshooting and ticket resolution workflows.

---

## Lab Overview

The lab environment simulates a small corporate IT network, including:

| Component | Hostname | Role | IP Address | Description |
|-----------|----------|------|------------|-------------|
| **DC01** | `DC01` | Domain Controller | 192.168.10.10 | Active Directory, DNS, DHCP |
| **Client01** | `Client01` | Workstation | DHCP | Domain-joined Windows 10 client |
| **Internal Network** | `LabNet` | Virtual Network | 192.168.10.0/24 | Isolated network for domain communication |

This setup replicates a realistic enterprise environment, allowing me to simulate real IT support scenarios with both client and server components connected within a controlled network.

---

## Jira Service Desk Setup

I configured a dedicated **Jira Service Management** project to manage IT support requests:

- Designed **custom request forms** to capture detailed user information.
- Created **queues** to organize incoming tickets efficiently.
- Defined **SLA targets** to simulate realistic response and resolution expectations.

---

## Tickets Worked & Troubleshooting

I created and resolved multiple IT support tickets, documenting every step:

1. [Password reset and account unlock](./01_Ticketing-System-Simulation-Lab/01_Password-Reset-Request)  
   - Reset Active Directory passwords and unlocked accounts, including verification of account functionality.

2. [Network printer not responding](./01_Ticketing-System-Simulation-Lab/02_Printer-Offline)
   - Diagnosed printer connectivity, restarted spooler services, and ensured proper driver installation.

3. [Domain join failure on a workstation](./01_Ticketing-System-Simulation-Lab/03_Domain-Join-Failure)
   - Investigated DNS and network settings, rejoined client machines to the domain.

4. [File access privilege change request](./01_Ticketing-System-Simulation-Lab/04_Permission-Change-Request)  
   - Configured NTFS permissions and shared folder access to grant appropriate user rights.

5. [User account locked out](./01_Ticketing-System-Simulation-Lab/05_User-Account-Locked-Out/screenshots)  
   - Verified account activity, unlocked user account, and documented resolution steps.

Each ticket includes a clear problem description, step-by-step troubleshooting, testing, and final resolution, demonstrating systematic problem-solving skills.

---

## Key Skills Demonstrated

- IT incident management and ticket workflow practices.
- Active Directory administration, including user and group management.
- Printer and network resource setup and troubleshooting.
- Networking diagnostics and DNS configuration.
- Clear documentation and communication of technical solutions.

---

## Knowledge Base (KB) Articles

**Objective:**  
To create practical, user-friendly KB articles for common IT issues, simulating real help desk documentation.  

**Articles Created:**

- **[01_How-To-Reset-Your-Password](./02_Knowledge-Base-Articles/01_How-To-Reset-Your-Password)**  
  Step-by-step instructions for resetting passwords, including complexity requirements and troubleshooting account lockouts.

- **[02_How-To-Install-a-Printer](./02_Knowledge-Base-Articles/02_How-To-Install-a-Printer)**  
  Guide to installing network printers manually or via Group Policy, including driver setup, test page printing, and common errors.

- **[03_How-To-Access-Remote-Support-Tools](./02_Knowledge-Base-Articles/03_How-To-Access-Remote-Support-Tools)**  
  Instructions for connecting using RDP, Quick Assist, or TeamViewer, including secure access and session logging.

- **[04_How-To-Map-a-Network-Drive](./02_Knowledge-Base-Articles/04_How-To-Map-a-Network-Drive)**  
  Detailed instructions for mapping shared folders via drive letters or UNC paths, ensuring persistent connections and troubleshooting common issues.

- **[05_How-To-Connect-To-VPN-And-Remote-Resources](./02_Knowledge-Base-Articles/05_How-To-Connect-To-VPN-And-Remote-Resources)**  
  Guide for securely connecting to the corporate network and internal resources using a VPN, with troubleshooting tips for authentication failures, limited access, and disconnects.

---

## Key Learnings

- Documenting IT workflows and solutions clearly reduces repetitive support requests and improves efficiency.
- Creating KB articles enhances communication skills while demonstrating technical expertise.
- Hands-on troubleshooting reinforces systematic problem-solving and technical decision-making.

---

## Deliverables

- Fully configured lab environment with domain controller, client workstation, and virtual network.
- Jira Service Desk project with multiple sample tickets and resolved issues.
- 3–5 professional Knowledge Base articles in Markdown format with step-by-step instructions and troubleshooting guidance.
- Complete documentation of IT support processes suitable for inclusion in a professional portfolio.

