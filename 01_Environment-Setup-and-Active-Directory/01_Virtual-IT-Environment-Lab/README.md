# Virtual IT Environment Setup (Active Directory Lab)

This project showcases how I built a fully functional, isolated Windows domain environment from scratch.  
The goal of this lab was to simulate a small corporate network that includes a domain controller, two client machines, and a delegated help desk administrator — all following real-world IT best practices.

---

## Overview

By the end of this project, I had the following setup:

| Component | Hostname | Role | IP Address | Description |
|------------|-----------|------|-------------|--------------|
| **DC01** | `DC01` | Domain Controller | 192.168.10.10 | AD DS, DNS, DHCP |
| **Client01** | `Client01` | Workstation | DHCP | Domain-joined client |
| **Client02** | `Client02` | Workstation | DHCP | Domain-joined client |
| **HDAdmin** | `HDAdmin` | Help Desk admin station | DHCP | Delegated Help Desk admin account |

I built this environment from scratch to strengthen my Active Directory, networking, and Windows Server administration skills.

---

## Step 1 — Preparing the Host and Network

Before installing anything, I designed a clean network layout to keep the lab isolated and realistic.

I created a new **Internal Network** in VirtualBox named `LabNet` and gave **DC01** two adapters:
- Adapter 1: **NAT** (for temporary internet access)
- Adapter 2: **Internal Network (LabNet)** for client communication

Clients only used the **LabNet** adapter so all DNS and DHCP traffic stayed within the lab.

![Screenshot - VirtualBox Network Setup](/screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)

This setup ensured I could manage updates on the server while keeping the environment contained — just like an enterprise subnet.

---

## Step 2 — Installing and Naming the Domain Controller

I installed **Windows Server 2022 (Desktop Experience)** on my first VM and set it up as the main server for the lab.  
After installation, I renamed the machine to **DC01** and rebooted it to make identification consistent across tools.

![Screenshot - Windows Server Installation](/screenshots/02_Server-Manager-&-Naming/Windows-Server-Installation.png)
![Screenshot - Renamed to DC01](/screenshots/02_Server-Manager-&-Naming/Renamed-to-DC01.png)

Using a descriptive name helps avoid confusion later when you start managing DNS zones, DHCP scopes, or Group Policy.

---

## Step 3 — Configuring Static IP on DC01

Domain controllers need fixed IPs, so I configured DC01’s internal adapter with:
- IP Address: 192.168.10.10
- Subnet Mask: 255.255.255.0
- DNS Server: 192.168.10.10

Then I verified it with `ipconfig /all` to confirm the address persisted after reboot.

![Screenshot - Network Setup](/screenshots/03_Network-Setup/DC01-Static-IP-Configuration.png)

This step ensures reliable DNS resolution for all future domain-joined clients.

---

## Step 4 — Promoting DC01 to a Domain Controller

Next, I installed the **Active Directory Domain Services (AD DS)** role and promoted the server to create a new forest named **corp.local**.

During setup, I also allowed the wizard to install **DNS**, since AD heavily depends on it.  
After the reboot, I logged in as `corp\Administrator`.

![Screenshot - Add Roles and Features (AD DS)](/screenshots/04_AD-DS-Configuration/Add-Roles-and-Features-(AD-DS,DNS,DHCP).png)  
![Screenshot - New Forest corp.local](/screenshots/04_AD-DS-Configuration/New-Forest-corp.local.png)  
![Screenshot - DNS Zone corp.local](/screenshots/04_AD-DS-Configuration/DNS-Zone-corp.local.png)

At this point, my domain and DNS services were fully operational.

---

## Step 5 — Setting Up DHCP on DC01

To automate IP assignments, I added the **DHCP Server** role.

I created a scope named **CorpScope** covering `192.168.10.100–192.168.10.200`, using:
- Subnet mask: `255.255.255.0`
- DNS: `192.168.10.10` (DC01)
- Gateway: blank (internal lab)

After authorizing DHCP in Active Directory, it was ready to hand out IPs to my clients.

![Screenshot - 01_DHCP Configuration](/screenshots/05_DHCP-Configuration/01_DHCP-Configuration.png)
![Screenshot - 02_DHCP Configuration](/screenshots/05_DHCP-Configuration/02_DHCP-Configuration.png)
![Screenshot - 03_DHCP Configuration](/screenshots/05_DHCP-Configuration/03_DHCP-Configuration.png)
![Screenshot - 04_DHCP Configuration](/screenshots/05_DHCP-Configuration/04_DHCP-Configuration.png)
![Screenshot - 05_DHCP Configuration](/screenshots/05_DHCP-Configuration/05_DHCP-Configuration.png)

---

## Step 6 — Creating Organizational Units and User Accounts

I opened **Active Directory Users and Computers (ADUC)** and created a clear, departmental structure:
```
_Users
 ├── IT
 ├── HR
 └── Sales
```
Then, I added several user accounts in their respective OUs:
- `jsmith` (IT)
- `mjohnson` (HR)
- `ahunter` (Sales)

![Screenshot - OU Structure](/screenshots/06_OU-Configuration/OU-Structure.png)  
![Screenshot - User Creation in ADUC](/screenshots/06_OU-Configuration/User-Creation-in-ADUC.png)

This setup mirrors how real companies structure their directories and delegate management.

---

## Step 7 — Setting Up and Joining Client Machines

Once DC01 was fully configured, I turned to my two client VMs.

Both were connected only to the **LabNet** adapter and set to obtain IPs automatically via DHCP.  
When I ran `ipconfig /all`, they correctly received IPs in the 192.168.10.x range and DNS set to 192.168.10.10.

![Screenshot - Client IP from DHCP](screenshots/client_ip_dhcp.png)  
![Screenshot - Domain Join](/screenshots/07_Domain-Join/01_Domain-Join-Successful.png)
![Screenshot - Domain Join Successful](/screenshots/07_Domain-Join/02_Domain-Join-Successful.png)
![Screenshot - Domain User Login](/screenshots/07_Domain-Join/Domain-User-Login.png)

I then joined **Client01** and **Client02** to the `corp.local` domain, verified the success messages, and logged in as one of my domain users.

After logging in, I ran:
- whoami
- ping dc01
- nslookup corp.local

![Screenshot - Connectivity Tests](/screenshots/07_Domain-Join/Connectivity-Tests.png)

All results confirmed domain connectivity and DNS functionality.

---

## Step 8 — Delegating Help Desk Permissions

To simulate a real Help Desk scenario, I created a new OU called `_DedicatedAdmins` and then made a new security group called **HelpDeskAdmins**.  
I added a user called **hdadmin** to that group.

Then, using the **Delegation of Control Wizard** in ADUC, I gave the HelpDeskAdmins group the ability to:
- Create and delete users  
- Reset passwords  
- Unlock accounts  

![Screenshot - 01_Help Desk User and Group](/screenshots/08_Delegating-Help-Desk-Permissions/01_Help-Desk-User-and-Group.png)
![Screenshot - 02_Help Desk User and Group](/screenshots/08_Delegating-Help-Desk-Permissions/02_Help-Desk-User-and-Group.png)  
![Screenshot - 03_Help Desk User and Group](/screenshots/08_Delegating-Help-Desk-Permissions/03_Help-Desk-User-and-Group.png)  
![Screenshot - 01_Delegation Wizard](/screenshots/08_Delegating-Help-Desk-Permissions/01_Delegation-Wizard.png)
![Screenshot - 02_Delegation Wizard](/screenshots/08_Delegating-Help-Desk-Permissions/02_Delegation-Wizard.png)
![Screenshot - 03_Delegation Wizard](/screenshots/08_Delegating-Help-Desk-Permissions/03_Delegation-Wizard.png)

This gave my Help Desk admin limited control over the user OUs without giving full domain privileges.  

Finally, on the Help Desk workstation, I installed **RSAT: Active Directory Domain Services and Lightweight Directory Tools** so the delegated admin could use ADUC remotely.

![Screenshot - RSAT Installed](/screenshots/08_Delegating-Help-Desk-Permissions/RSAT-Installe.png)

I tested the permissions by logging in as `corp\hdadmin` and everything was working as intended.

---

## Step 9 — Enabling Remote Management

For easier administration, I enabled **Remote Desktop** and **PowerShell Remoting** on all machines.  
This allowed me to connect between VMs just like a sysadmin would in production.

![Screenshot - 01_Remote Desktop Enabled](/screenshots/09_Enabling-Remote-Management/01_Remote-Desktop-Enabled.png)
![Screenshot - 02_Remote Desktop Enabled](/screenshots/09_Enabling-Remote-Management/02_Remote-Desktop-Enabled.png)

---

## Step 10 — Taking Snapshots and Finalizing the Lab

Once everything was working, I took snapshots of each VM to save the environment state.

This ensures I can always revert to a clean baseline before experimenting further.

![Screenshot - Snapshot](/screenshots/10_Snapshot/VirtualBox-Snapshots.png)

---

## Conclusion

This lab taught me a lot about planning and implementing Active Directory from networking to domain services to delegation.  
It reflects how I approach IT work: structured, detail-oriented, and focused on understanding **why** each configuration matters, not just how to do it.
