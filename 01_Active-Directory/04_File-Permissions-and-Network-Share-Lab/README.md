# File Permissions & Network Share Management
The goal of this lab was to understand how **file sharing and access control** work in a domain environment — specifically how NTFS and share-level permissions interact.

This is a core skill for both Help Desk and Systems Administrator roles, as it directly affects how users access shared company resources.

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

## Step 1 — Create and Share a Folder

**Purpose:** Set up a shared folder that users across the domain can access.

- On `DC01`, created a folder `C:\Shared`.
- Right-clicked → **Properties → Sharing → Advanced Sharing** → checked **Share this folder**.
- Shared name: `Shared`
- Permissions:
  - Removed “Everyone”
  - Added **Authenticated Users → Read**
  - Added **IT_Staff → Change, Read**

[Sharing-Permissions-Authenticated-Users](./screenshots/01_Sharing-Permissions-Authenticated-Users.png)

[Sharing-Permissions-Help-Deskd](./screenshots/02_Sharing-Permissions-Help-Desk.png)

---

## Step 2 — Configure NTFS Permissions

**Purpose:** Combine share and NTFS permissions for layered security.

- Right-clicked the folder → **Properties → Security**.
- Ensured **Administrator** retained full control.
- Granted **IT_Staff** → Modify, Read & Execute, List Folder Contents, Read, Write.
- Granted **HR_Staff** → Read-only permissions.

[NTFS-Permissions-Help-Desk](./screenshots/03_NTFS-Permissions-Help-Desk.png)

[NTFS-Permissions-Authenticated-Users](./screenshots/04_NTFS-Permissions-Authenticated-Users.png)

---

## Step 3 — Test Access and Map Network Drive on Client Machine

**Purpose:** Verify that permissions apply as intended and test drive mapping.

- Logged into `Client01` as `corp\jsmith` (member of IT_Staff).
- Opened File Explorer → `\\DC01\Shared`.
- Verified:
  - Read, write, and modify permissions worked correctly for IT_Staff.
  - HR_Staff users could open but not modify files.

**Mapped the drive manually:**
- In File Explorer, right-clicked **This PC → Map network drive...**
- Selected **Drive letter:** `Z:`
- Entered **Folder path:** `\\DC01\Shared`
- Checked **Reconnect at sign-in**
- Clicked **Finish**

[Mapping-Wizard](./screenshots/05_Mapping-Wizard.png)

[Mapped-Network-Drive](./screenshots/06_Mapped-Network-Drive.png)

[Sucssessful-Modification-From-Help-Desk](./screenshots/07_Sucssessful-Modification-From-Help-Desk.png.png)

[Permission-Error-From-HR](./screenshots/08_Permission-Error-From-HR.png)

---

## Outcome

By the end of this lab, I had a fully functioning **shared folder infrastructure** with properly configured permissions and access testing across user roles.  
This lab strengthened my understanding of how **NTFS** and **share permissions** complement each other.

