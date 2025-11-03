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

📸 **Screenshot #1:** Folder Sharing permissions showing `Authenticated Users` (Read) and `IT_Staff` (Change, Read).

---

## Step 2 — Configure NTFS Permissions

**Purpose:** Combine share and NTFS permissions for layered security.

- Right-clicked the folder → **Properties → Security**.
- Ensured **Administrator** retained full control.
- Granted **IT_Staff** → Modify, Read & Execute, List Folder Contents, Read, Write.
- Granted **HR_Staff** → Read-only permissions.

📸 **Screenshot #2:** Folder Security tab showing NTFS permissions for both `IT_Staff` and `HR_Staff`.

---

## Step 3 — Test Access from Client Machine

**Purpose:** Verify that permissions apply as intended.

- Logged into `Client01` as `corp\jsmith` (member of IT_Staff).
- Opened File Explorer → `\\DC01\Shared`.
- Verified:
  - Read, write, and modify permissions worked correctly for IT_Staff.
  - HR_Staff users could open but not modify files.

📸 **Screenshot #3:** Client01 showing successful access by IT_Staff user.
📸 **Screenshot #4:** Error message when HR_Staff attempts to modify a file (permission denied).

---

## Step 4 — Test Group Policy Drive Mapping Integration

**Purpose:** Validate integration with the Group Policy lab.

- Verified that the shared folder could be mapped via the `Corp Network Drives` GPO created earlier.
- Confirmed users automatically received drive `Z:` → `\\DC01\Shared`.

📸 **Screenshot #5:** File Explorer showing mapped `Z:` drive (via GPO).

---

## Outcome

By the end of this lab, I had a fully functioning **shared folder infrastructure** with properly configured permissions and access testing across user roles.  
This lab strengthened my understanding of how **NTFS** and **share permissions** complement each other.

