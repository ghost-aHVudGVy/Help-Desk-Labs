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

**Screenshot 1:** ADUC console open with the `corp.local` domain expanded.
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)

---

## Step 2 — Creating a New User Account

Inside my organizational unit, I created a new user to simulate onboarding a new employee.  
I entered the user details and set an initial password policy requiring a password change at next logon.

**Screenshot 2:** Final screen of the “New Object – User” wizard.  
**Screenshot 3:** ADUC showing the newly created user listed in the OU.
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)

---

## Step 3 — Disabling and Re-enabling an Account

Next, I tested lifecycle control by disabling the same user account to simulate a temporary suspension.  
After confirming the status change icon in ADUC, I re-enabled the account to restore access.

**Screenshot 4:** User account in a disabled state (icon with downward arrow).
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)


---

## Step 4 — Resetting and Unlocking a Password

To simulate a Help Desk support scenario, I performed a password reset and forced the user to change it at next logon.  
I also tested account lockout by intentionally entering incorrect credentials multiple times, then unlocked the account.

**Screenshot 5:** Reset Password dialog box displayed in ADUC.
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)

---

## Step 5 — Creating and Managing Security Groups

Finally, I created new security groups (Sales Manager) to practice role-based access control.  
I added the user I've created in the first step users to the group and verified group membership through the **Members** tab.

**Screenshot 6:** Group Properties window showing multiple members.
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)
[Screenshot - VirtualBox Network Setup](./screenshots/01_VirtualBox-Network-Setup/VirtualBox-Network-Setup.png)

---

## Conclusion

This lab reinforced key administrative skills in **user lifecycle management** within Active Directory.  
By completing it, I gained practical experience with the same tools and workflows used in real IT environments. From provisioning and access control to password resets and group administration.

All configuration steps and verification screenshots are documented here to illustrate both the process and the outcome.

---


