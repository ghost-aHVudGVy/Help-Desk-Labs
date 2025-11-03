# Active Directory & IT Infrastructure Lab

## Overview
This project consists of four hands-on labs that simulate real-world IT administration tasks within a Windows Server domain environment.  
Each lab builds upon the previous one, starting from infrastructure setup and progressing to user management, Group Policy configuration, and secure file sharing.  
Together, they demonstrate a full workflow of how Active Directory environments are deployed, managed, and maintained in enterprise settings.

---

## 01_Virtual IT Environment Setup

In this lab, I built a fully functional Windows domain environment from scratch to replicate a small corporate network.  
The setup included:

- **Domain Controller (DC01)** – running Active Directory Domain Services (AD DS), DNS, and DHCP  
- **Two Client Machines (Client01 & Client02)** – domain-joined workstations  
- **Delegated Help Desk Admin (HDAdmin)** – a limited administrative account for testing permissions

To keep the environment realistic and secure, I designed an isolated internal network in VirtualBox. DC01 managed all essential network services, including IP addressing through DHCP and name resolution through DNS.

Once the infrastructure was ready, I:

- Created a **new Active Directory forest** (`corp.local`)  
- Structured the directory with **Organizational Units** for IT, HR, and Sales departments  
- **Joined both clients** to the domain and verified DNS, domain connectivity, and user logins  
- Configured a **Help Desk administrative account** with delegated permissions to manage users, reset passwords, and unlock accounts  
- Tested remote management using **RSAT tools** and confirmed access control worked as expected

This project gave me a strong, hands-on understanding of how **Active Directory, DNS, and DHCP** interact within a corporate environment. It also reinforced the importance of structured planning, secure delegation, and documentation.

---

## 02_User Account Management Lab

This lab focused on developing hands-on experience with essential Active Directory administration.
The goal was to practice creating, managing, and troubleshooting user accounts in a simulated corporate environment.

The lab took place within the domain setup from my previous project, which included a Windows Server domain controller (DC01) and a domain-joined Windows 10 workstation (Client01), both running on an isolated internal network.

I began by using the **Active Directory Users and Computers (ADUC)** console on DC01 to explore the domain structure and manage organizational units. From there, I worked through the core lifecycle of user management:

- **Created new user accounts** to simulate employee onboarding and configured password policies requiring password changes at first logon  
- **Disabled and re-enabled accounts** to represent temporary suspensions and reinstatements  
- **Reset and unlocked passwords** to mirror real Help Desk support scenarios where users forget or lock themselves out  
- **Created and managed security groups** to apply role-based access control and verified group membership in ADUC

By the end of this lab, I had a complete understanding of how user and group management operates in Active Directory, from account provisioning and access control to password resets and security delegation.  
This reinforced my ability to handle everyday administrative tasks confidently and accurately, following standard IT support practices.

---

## 03_Group Policy Management Lab

This lab focused on mastering **Group Policy Management** — learning how to create, link, and apply domain-wide policies that shape both security and user experience.

I configured and tested three key GPOs:

- **Desktop Wallpaper Policy:** Created and linked a domain-level GPO that automatically applied a company-branded wallpaper for all users, confirming that user environment settings propagate correctly through Active Directory.
- **Password Policy:** Updated the Default Domain Policy to enforce stronger password requirements — including a minimum of eight characters, complexity rules, and a 60-day expiration — mirroring real organizational security standards.
- **Mapped Network Drive Policy:** Created a GPO that automatically mapped a shared folder (`\\DC01\Shared`) as drive **Z:** for all domain users, reducing manual setup and ensuring consistent access to shared resources.

This lab demonstrated practical use of Group Policy to automate configuration, strengthen security, and standardize the IT environment across all clients.

---

## 04_File Permissions & Network Share Management

This lab focused on managing shared folders and permissions in a Windows domain environment.

- Created a shared folder (`C:\Shared`) on **DC01** and set proper **share permissions** for Authenticated Users and IT_Staff.  
- Configured **NTFS permissions** to give IT_Staff modify rights and HR_Staff read-only access.  
- Tested access from **Client01** to confirm permissions worked as intended.  
- Mapped the shared folder as a **network drive (Z:)** for easy access.

With this lab I gained hands-on experience setting up and securing shared network resources using both NTFS and share-level permissions.

---

## Outcome

By the end of this project, I had:

- Built a functioning Active Directory domain from scratch.  
- Configured DNS, DHCP, and Group Policy management.  
- Managed user accounts and security groups through ADUC.  
- Applied GPOs for security and usability.  
- Implemented file sharing with proper access control.  

Through this process, I developed not just technical skill, but a stronger sense of **how IT systems are structured, secured, and maintained** in real-world environments.

*This lab represents my foundational work in system administration, combining hands-on configuration, structured documentation, and professional presentation.*
