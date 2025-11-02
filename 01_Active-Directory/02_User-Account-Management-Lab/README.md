# User Account Management

This lab focused on building hands-on experience with essential **Active Directory (AD)** administration tasks that every Help Desk or IT Support technician performs daily.  
The goal was to practice creating and managing domain user accounts, handling password operations, and organizing users into security groups.

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

## Step 1 — Accessing Active Directory Users and Computers

I started by logging into **DC01** as the domain administrator and launching the **Active Directory Users and Computers (ADUC)** console.  
After expanding the domain tree, I verified the existing structure and navigated to my dedicated Organizational Units.

[Screenshot - ADUC-Console](./screenshots/01_ADUC-Console.png)

---

## Step 2 — Creating a New User Account

Inside my organizational unit, I created a new user to simulate onboarding a new employee.  
I entered the user details and set an initial password policy requiring a password change at next logon.

[Screenshot - New-User-Wizard](./screenshots/02_New-User-Wizard.png)
[Screenshot - User-Created](./screenshots/03_User-Created.png)

---

## Step 3 — Disabling and Re-enabling an Account

Next, I tested lifecycle control by disabling the same user account to simulate a temporary suspension.  
After confirming the status change icon in ADUC, I re-enabled the account to restore access.

[Screenshot - Account-Disabled](./screenshots/04_Account-Disabled.png)
[Screenshot - Account-Reenabled](./screenshots/05_Account-Reenabled.png)

---

## Step 4 — Resetting and Unlocking a Password

To simulate a Help Desk support scenario, I performed a password reset and forced the user to change it at next logon.  
I also tested account lockout by intentionally entering incorrect credentials multiple times, then unlocked the account.

[Screenshot - Reset-Password](./screenshots/06_Reset-Password.png)
[Screenshot - Account-Unlock](./screenshots/07_Account-Unlock.png)

---

## Step 5 — Creating and Managing Security Groups

Finally, I created new security groups (Sales Manager) to practice role-based access control.  
I added the user I've created in the first step users to the group and verified group membership through the **Members** tab.

[Screenshot - New-Group-Wizard](./screenshots/08_New-Group-Wizard.png)
[Screenshot - Group-Member-Added](./screenshots/09_Group-Member-Added.png)

---

## Conclusion

This lab provided me with practical experience in Active Directory, where I managed the full user lifecycle.

By completing it, I gained practical experience with the same tools and workflows used in real IT environments. From provisioning and access control to password resets and group administration.

---


