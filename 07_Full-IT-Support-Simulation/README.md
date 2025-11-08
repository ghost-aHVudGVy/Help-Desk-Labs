# End-to-End Help Desk Onboarding Simulation

This lab project simulates the full onboarding workflow for a new employee in a Windows domain environment.

---

## Overview

By the start of this lab, the following environment was already set up and running:

| Component | Hostname | Role | IP Address | Description |
|------------|-----------|------|-------------|--------------|
| **DC01** | `DC01` | Domain Controller | 192.168.10.10 | Active Directory Domain Services, DNS, DHCP |
| **Client01** | `Client01` | Workstation | DHCP | Domain-joined Windows 10 client |
| **Internal Network** | `LabNet` | Virtual Network | 192.168.10.0/24 | Isolated internal network used for domain communication |

This setup replicates a small corporate environment, with both machines connected through an isolated internal network to simulate a real enterprise domain.

---

## Scenario

A new employee joined the company and required full IT onboarding.  
I completed the setup as follows:

1. Created a new user account in **Active Directory**
2. Configured the account
3. Created a new **Security Group (IT_Staff)** and added the user
4. Applied folder and printer access automatically using **Group Policy Objects (GPOs)** tied to that security group
5. Logged in as the new user to verify access to shared resources and printing
6. Documented the full workflow inside the ticketing system

---

## Step-by-Step Process

### 1. Created the User Account in Active Directory

I created the new user account in **Active Directory Users and Computers**, assigned an initial password, and prepared the account for first login.

[Creating the account](./screenshots/01_Creating_The_Account.png)

[Setting the password](./screenshots/02_Setting_The_Password.png)

---

### 2. Created and Assigned Security Group Membership

I created the **IT_Staff** security group to represent users who require access to departmental shared drive space and printers.  
The new user was added to this group.

[Creating the security group](./screenshots/03_Creating-Security-Group.png)

[Adding the user to the group](./screenshots/04_Added-The-User-To-The-Group.png)

---

### 3. Configured Shared Folder Permissions

I configured permissions at both the **share** and **NTFS** levels to ensure proper access control.  
Members of *IT_Staff* were granted appropriate read/write permissions.

[Granting share permissions](./screenshots/05_Granting-Shared=Permissions.png)

[Granting NTFS permissions](./screenshots/06_Granting-NTFS-Permissions.png)

---

### 4. Logged In as the New User and Verified Access

I logged into the workstation as the new user to confirm profile creation, authentication, and baseline access.

[Logging in as the new user](./screenshots/07_Logging-With-The-New-User.png)

---

### 5. Automated Drive Mapping via Group Policy

To avoid manual mapping and to ensure consistent access across machines, I created a **GPO** that automatically maps the departmental shared drive whenever a user in the **IT_Staff** group logs in.

[Created GPO for automatic drive mapping](./screenshots/08_Creted-GPO-For-Automatic-Drive-Mapping.png)

[Configuring drive mapping in GPO](./screenshots/09_Creating-GPO-Mapping-Drive.png)

[Forcing policy update](./screenshots/10_Updating-The-Policies.png)

[Drive successfully mapped](./screenshots/11_Shared-Drive-Aveable.png)

---

### 6. Configured Office Printer Access via GPO

I added the office printer and deployed it via GPO so that users in the **IT_Staff** group automatically receive the printer connection when they log in.

[Adding printer via GPO](./screenshots/12_Adding-The-Office-Printer-Through-GPO.png)

[Printer successfully installed](./screenshots/13_Office-Printer-Added-Through-GPO.png)

---

## What This Demonstrates

This lab demonstrates the ability to:

- Manage users and security groups in **Active Directory**
- Apply **least privilege access control** using share and NTFS permissions
- Use **Group Policy Objects** to automate workstation configuration and user experience
- Verify successful configuration from the end-user perspective
- Maintain consistent internal documentation and ticket history

---

## Summary

This onboarding simulation reflects a complete support workflow from account provisioning to workstation readiness.

The result:  
A new user can sign in, access the correct shared files, and print to the appropriate office printer—without manual setup on each workstation.
