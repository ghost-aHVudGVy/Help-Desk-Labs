# IT Help Desk & Systems Administration Lab Portfolio
**Practical IT Support & Troubleshooting Portfolio**

**Disclaimer:** All labs are performed in a **controlled, educational environment**. No unauthorized systems or networks are accessed. The purpose of this repository is to demonstrate ethical, professional IT skills only. You can find very detailed information with screenshots on each of those labs here is just the summery.

## Introduction

This lab series documents my hands-on experience building and managing a **Windows domain environment** from scratch. The labs cover core IT tasks, including:

- **Active Directory:** user and group management, delegation, permissions  
- **Group Policy:** configuration, drive mapping, desktop standardization  
- **File & Print Services:** shared folders, NTFS/share permissions, print server deployment  
- **Network & Remote Access:** VPN, RDP, network diagnostics, troubleshooting  
- **IT Support Workflows:** ticketing, KB articles, onboarding simulations  

Each lab simulates **real-world corporate IT scenarios**, emphasizing best practices, verification, and structured documentation.

---

### 1.Virtual IT Environment Setup (Active Directory Lab)

This lab focused on building a fully functioning Windows domain environment from the ground up. The goal was to simulate a small company network and establish the core infrastructure used for identity management, workstation access, and administrative control.

**Environment Setup**

| Hostname  | Role                       | IP Address       | Notes                               |
|----------|----------------------------|------------------|-------------------------------------|
| DC01     | Domain Controller (AD, DNS, DHCP) | 192.168.10.10   | Core server for identity and network services |
| Client01 | Windows 10 Workstation     | DHCP (LabNet)    | Joined to the domain                |
| Client02 | Windows 10 Workstation     | DHCP (LabNet)    | Joined to the domain                |
| HDAdmin  | Help Desk Admin Workstation| DHCP (LabNet)    | Used for delegated AD management    |

**Key Configuration Steps**

- Created an isolated internal network in VirtualBox to contain all domain traffic.
- Installed Windows Server 2022 and configured it as `DC01` with a static IP.
- Promoted the server to a domain controller and created the domain: `corp.local`.
- Configured DNS and DHCP on the domain controller to automatically assign IP addresses to clients.
- Created Active Directory Organizational Units (IT, HR, Sales) and added user accounts to each.
- Joined Client01 and Client02 to the `corp.local` domain and confirmed connectivity using domain logins and network tests.
- Created a HelpDeskAdmins security group and delegated limited administrative permissions (password resets, user creation/deletion, account unlock).
- Installed RSAT tools on the help desk workstation to allow remote directory management.
- Enabled Remote Desktop and PowerShell remoting for administrative access.
- Took VM snapshots to preserve the environment for future labs and troubleshooting practice.

This setup provided the foundation for all following labs, forming a controlled and realistic environment to practice user management, permissions, Group Policy, and troubleshooting workflows.

---

### 2.Active Directory User Account Management Lab

In this lab, I focused on practical user management in Active Directory, simulating real Help Desk tasks.

**What I Did**

- **Created new user accounts** and set initial passwords.  
- **Disabled, re-enabled, and deleted accounts** to practice the user lifecycle.  
- **Reset passwords and unlocked accounts** for typical support scenarios.  
- **Managed security group membership** to enforce role-based access.

**Skills Gained**

- User account lifecycle management  
- Password handling and account lockout resolution  
- Role-based access control and group management  
- Hands-on experience with Active Directory administration

---

### 3.Group Policy Management Lab

In this lab, I focused on creating, linking, and applying Group Policies in a Windows domain environment to enforce security and standardize user settings.

**What I Did**

- **Created and applied a desktop wallpaper GPO** to standardize the user environment across the domain.  
- **Configured password policies** in the Default Domain Policy to enforce complexity, minimum length, and expiration rules.  
- **Mapped network drives via GPO** by creating a shared folder on the server and configuring a drive mapping policy for domain users.  
- **Tested and verified GPO application** on client machines to ensure policies were applied correctly.

**Skills Gained**

- Designing and linking Group Policies in Active Directory  
- Enforcing domain-wide security standards through password policies  
- Automating user environment setup, such as mapped drives and desktop settings  
- Validating and troubleshooting GPOs to confirm proper deployment  

---

### 4.File Permissions & Network Share Management Lab

In this lab, I focused on configuring file shares and managing access permissions in a Windows domain environment.

**What I Did**

- **Created a shared folder** on the domain controller for domain users.  
- **Configured share-level permissions** to control access for different user groups (Authenticated Users, IT_Staff).  
- **Set NTFS permissions** to layer security, granting appropriate rights to IT_Staff, HR_Staff, and Administrators.  
- **Tested access** from a client machine to ensure users had the correct read/write/modify permissions.  
- **Mapped the shared folder** as a network drive on the client machine to verify functionality.

**Skills Gained**

- Understanding the interaction between NTFS and share permissions  
- Managing role-based access to shared resources  
- Testing and troubleshooting permission configurations  
- Mapping network drives for end-user access

---

### 5.Print Server Deployment & Group Policy Lab

In this lab, I configured a Windows Print Server and deployed a virtual printer to client machines using Group Policy, simulating a real enterprise setup.

**What I Did**

- **Installed the Print Server role** on the domain controller (DC01) and verified the Print Spooler service.  
- **Created a virtual printer** using a simulated TCP/IP port and shared it on the network.  
- **Tested manual printer connection** from a client machine to ensure network connectivity, permissions, and driver installation worked correctly.  
- **Deployed the printer via Group Policy** for automatic distribution to users in the domain.  
- **Verified functionality** by printing a test page and monitoring the print queue.  
- **Performed troubleshooting checks** including Print Spooler status, firewall rules, driver permissions, and network connectivity.

**Skills Gained**

- Managing print services in Windows Server  
- Deploying printers automatically with Group Policy  
- Testing and troubleshooting printer connectivity and permissions  
- Simulating enterprise print management without physical hardware

---

### 6.Remote Access & Support Tools Lab

In this lab, I focused on configuring and testing remote access tools to manage domain computers and simulate IT support scenarios.

**What I Did**

- **Enabled and tested Remote Desktop (RDP)** on both the domain controller and client machine for secure remote management.  
- **Verified connectivity and service status** using PowerShell and Remote Desktop Connection.  
- **Simulated a remote support session** and documented it in a structured support log, including session details, actions taken, and outcomes.  
- **Prepared the environment for additional remote tools** such as TeamViewer and Quick Assist, using the same configuration and verification principles.

**Skills Gained**

- Configuring and troubleshooting RDP for domain-joined machines  
- Creating structured support logs for IT documentation  
- Ensuring secure remote connectivity within a Windows domain  
- Understanding the workflow for remote user support and monitoring

---

### 7.Network Diagnostics & Troubleshooting Lab

In this lab, I focused on diagnosing and resolving network connectivity issues within a Windows domain environment.

**What I Did**

- **Checked IP configuration** on the client machine to confirm adapter and DNS settings.  
- **Tested connectivity** to the domain controller using ping.  
- **Verified DNS resolution** using nslookup.  
- **Traced network routes** with tracert to ensure proper packet flow.  
- **Simulated a DNS misconfiguration** by setting an invalid DNS address, then identified and corrected the issue.  
- **Documented the troubleshooting process** in a structured log to mimic real-world IT support workflow.

**Skills Gained**

- Step-by-step network diagnostics using ping, ipconfig, nslookup, and tracert  
- Identifying and resolving DNS and connectivity issues  
- Structured documentation of troubleshooting actions  
- Building a methodical approach to network problem-solving

---

### 8.VPN Configuration & Connectivity Troubleshooting Lab

In this lab, I configured VPN access and practiced troubleshooting common user connection issues within a Windows domain environment.

**What I Did**

- **Configured VPN services** on the server using RRAS and assigned internal IP addresses to clients.  
- **Enabled user dial-in permissions** in Active Directory to allow VPN authentication.  
- **Configured a Windows client VPN profile** and tested connectivity to internal resources.  
- **Simulated common issues**, including incorrect credentials and DNS resolution failures, and resolved them.  
- **Documented troubleshooting steps** and outcomes to mimic real-world IT support workflow.

**Skills Gained**

- Setting up and managing RRAS and VPN services on Windows Server  
- Managing user authentication and dial-in permissions  
- Diagnosing VPN connectivity and DNS issues  
- Testing network connectivity and verifying internal resource access  
- Creating structured documentation for support cases

---

### 9.Ticketing System Simulation Lab

In this lab, I simulated a real IT service desk workflow using Jira Service Management within a Windows domain environment.

**What I Did**

- **Configured a service desk project** in Jira with custom request forms, ticket queues, and SLA targets.  
- **Created and resolved common IT support tickets**, including password resets, account unlocks, printer issues, domain join failures, and file access requests.  
- **Documented each ticket** with problem description, troubleshooting steps, verification, and resolution notes.  
- **Followed professional workflow practices** to mimic real-world incident management.

**Skills Gained**

- Incident management and ticket workflow  
- Clear technical documentation and communication  
- Active Directory user and policy administration  
- Printer and network resource troubleshooting  
- Root-cause analysis and systematic problem-solving

---

### 10.Knowledge Base (KB) Documentation Lab

In this lab, I created practical Knowledge Base articles to support end-users and streamline IT support processes.

**What I Did**

- **Wrote 5 KB articles** covering common IT support tasks, including:  
  - Resetting Active Directory passwords  
  - Installing network printers (manual and via Group Policy)  
  - Accessing remote support tools (RDP)  
  - Mapping network drives  
  - Connecting to VPN and internal resources  
- **Included step-by-step instructions** with troubleshooting guidance for each task.  
- **Focused on user clarity**, ensuring content was accessible for varying technical skill levels.  
- **Prepared the articles** in Markdown format, complete with screenshots and practical notes.

**Skills Gained**

- Translating technical procedures into clear, user-friendly documentation  
- Reducing repetitive support requests through structured KB content  
- Enhancing workflow efficiency with professional IT documentation  
- Demonstrating both technical knowledge and communication skills

---

### 11.End-to-End Help Desk Onboarding Simulation Lab

In this capstone lab, I simulated the full IT onboarding workflow for a new employee in a Windows domain environment.

**What I Did**

- **Created a new user account** in Active Directory and configured initial login settings.  
- **Set up a security group (IT_Staff)** and added the new user to manage access control.  
- **Configured shared folder permissions** (NTFS and share-level) for departmental access.  
- **Automated network drive mapping** via Group Policy for the IT_Staff group.  
- **Deployed office printer access** automatically using Group Policy.  
- **Verified the setup** by logging in as the new user and confirming access to files, drives, and printers.  
- **Documented the entire workflow** in the ticketing system to reflect a real-world support process.

**Skills Gained**

- Managing users and security groups in Active Directory  
- Applying least-privilege access control with NTFS and share permissions  
- Automating user environment setup using Group Policy  
- End-to-end verification of user access and workstation readiness  
- Professional documentation of IT support workflows

---

## Conclusion

Through these labs, I developed practical skills in:

- **System administration:** managing users, groups, permissions, and services  
- **Automation:** applying policies and automating user setup via GPO  
- **Troubleshooting:** diagnosing network, VPN, and access issues methodically  
- **IT support processes:** ticket management, KB documentation, onboarding workflows  

This hands-on experience demonstrates **real-world IT proficiency**, combining technical execution with professional documentation and workflow management.

---

## Certifications  
- CompTIA A+  
- CompTIA Security+  

---

## Connect  
- **LinkedIn:** [www.linkedin.com/in/antonio-karadenizov](www.linkedin.com/in/antonio-karadenizov)  
- **GitHub:** [github.com/ghost-aHVudGVy](https://github.com/ghost-aHVudGVy)
