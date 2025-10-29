# Virtual IT Environment Setup

### Overview
This lab lays the foundation for my entire Help Desk Lab environment.  
Here, I built a small, fully functional virtual network that simulates a real corporate setup — complete with a **Windows Server domain controller**, **DNS/DHCP services**, and **two Windows 10 clients** joined to the domain.  

The goal was to understand how IT environments are structured, how devices communicate, and how Active Directory ties it all together.

---

### Objectives
- Create a virtual lab network that mirrors a small business environment  
- Configure a Windows Server as a **Domain Controller, DNS, and DHCP** server  
- Set up Windows 10 clients and join them to the domain  
- Validate network and domain connectivity  
- Prepare a stable base for all future Help Desk labs  

---

### Environment Setup
| Component | Role | Hostname | IP Address | Notes |
|------------|------|-----------|-------------|-------|
| Windows Server 2022 | Domain Controller (AD DS, DNS, DHCP) | DC01 | 192.168.10.10 | Core of the network |
| Windows 10 Client | Workstation #1 | Client01 | DHCP assigned | Joined to domain |
| Windows 10 Client | Workstation #2 | Client02 | DHCP assigned | Joined to domain |
| Network | Internal (LabNet) | — | 192.168.10.0/24 | Simulated LAN |

All machines were set up using **VirtualBox**, with one NAT adapter (for updates) and one Internal Network adapter (`LabNet`) for domain communication.

---

### Steps & Configuration Summary

#### 1. Server Setup
- Installed Windows Server 2022  
- Renamed the machine to **DC01** and set a static IP (`192.168.10.10`)  
- Installed and configured:
  - **Active Directory Domain Services (AD DS)**
  - **DNS Server**
  - **DHCP Server**
- Promoted the server to a **domain controller** for `corp.local`

#### 2. Active Directory Setup
- Created organizational units (OUs): `_Users`, `IT`, `HR`, `Sales`  
- Created several test user accounts under the correct OUs  
- Verified login with domain credentials  

#### 3. DHCP & DNS Configuration
- Created DHCP scope (`192.168.10.100–200`)  
- Confirmed clients received IPs automatically  
- Verified DNS resolution for `corp.local` and `dc01.corp.local`

#### 4. Client Setup
- Installed Windows 10 on two clients  
- Joined both machines to the domain `corp.local`  
- Verified user logins and domain communication  
- Tested basic connectivity with `ping`, `nslookup`, and `whoami`

#### 5. Validation
- Confirmed clients appeared in **Active Directory Users and Computers (ADUC)**  
- Verified DHCP leases for both workstations  
- Tested DNS lookups for domain and hostnames  
- Created snapshot: *Base Environment – Domain Ready*

---

### Key Learnings
- Setting up a domain from scratch clarified how **Active Directory**, **DNS**, and **DHCP** work together.  
- Configuring static IPs and scopes helped reinforce IP planning and subnetting basics.  
- Joining clients to a domain showed how authentication flows through the network.  
- Documenting each step taught me the importance of **clear communication** and **attention to detail** — skills that matter in every IT support role.

---

### Screenshots
*(All screenshots are stored in the `screenshots/` folder)*  

| Step | Description |
|------|--------------|
| 01_virtualbox_network.png | VirtualBox network configuration for the lab |
| 02_dc01_installation_complete.png | Windows Server installation complete |
| 03_dc01_ipconfig.png | Static IP set on DC01 |
| 04_add_roles_ad.png | Adding AD DS and DNS roles |
| 05_domain_creation.png | Creating new forest `corp.local` |
| 06_server_manager_roles.png | Domain Controller roles installed |
| 07_dns_zone.png | DNS forward lookup zone for `corp.local` |
| 08_dhcp_install.png | Installing DHCP role |
| 09_dhcp_scope.png | DHCP scope configuration |
| 10_ou_structure.png | Active Directory OU structure |
| 11_new_user_creation.png | Creating user accounts in ADUC |
| 12_user_list_aduc.png | User list in Organizational Units |
| 13_client_dhcp_ipconfig.png | Client receiving IP from DHCP |
| 14_domain_join_window.png | Domain join dialog on Client01 |
| 15_domain_join_success.png | Successful domain join confirmation |
| 16_login_domain_user.png | Logging into domain account |
| 17_domain_connectivity.png | Ping, whoami, and nslookup verification |
| 18_dhcp_leases.png | DHCP lease entries for both clients |
| 19_computer_objects.png | Clients appearing in AD Computers container |
| 20_snapshot_created.png | Final VirtualBox snapshot for backup |

---

### Reflection
This lab gave me a strong foundation for understanding how enterprise IT environments are structured and managed.  
Building everything manually — from the server configuration to domain joins — helped me connect the dots between theory and real-world Help Desk work.  

Everything I build next (user management, GPOs, ticketing systems, troubleshooting scenarios) will build on this setup.

---

### Next Lab
[User Account Management Lab](./01_Environment-Setup-and-Active-Directory/02_User-Account-Management-Lab)

