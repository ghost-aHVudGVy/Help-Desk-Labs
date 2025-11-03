# Active Directory & IT Infrastructure Lab

This project demonstrates my ability to design, build, and manage a fully functional Active Directory environment — the kind of setup used in real corporate IT systems.  
I created everything from scratch to understand how domains, users, permissions, and group policies operate together in a secure and structured way.

---

## Phase 1: Environment Setup

I began by setting up a complete virtual IT environment using **VirtualBox**, configured to replicate a small business network.  
The setup included:

- **Windows Server 2022 (DC01)** — configured as a Domain Controller, DNS, and DHCP server.  
- **Windows 10 Client (Client01)** — joined to the domain for testing.  
- A dedicated internal subnet ensuring isolated, enterprise-style connectivity.

This phase built the technical foundation for everything that followed — verifying domain communication, DHCP leases, and name resolution across devices.

---

## Phase 2: Active Directory User Management

Once the environment was stable, I focused on **Active Directory administration** — the daily work of most IT support teams.

I created and managed user accounts, grouped them by department, and applied consistent naming conventions.  
To simulate real help desk workflows, I practiced resetting passwords, unlocking accounts, and assigning users to security and distribution groups.  
I also documented these procedures in a **Standard Operating Procedure (SOP)** to ensure they could be repeated reliably in any environment.

This phase strengthened my understanding of user lifecycle management and domain hygiene.

---

## Phase 3: Group Policy Management

Next, I worked on **centralized configuration using Group Policy Objects (GPOs)**.

I created and linked several policies that applied to all users and computers in the domain:
- A **desktop wallpaper policy** to standardize user environments.
- A **password policy** enforcing complexity, minimum length, and expiration.
- A **network drive mapping policy** that automatically connected users to a shared folder upon login.

After testing on the client machine, I confirmed that all policies deployed successfully through `gpupdate /force`.  
This phase gave me hands-on experience with how organizations enforce consistency and security at scale through GPOs.

---

## Phase 4: File Permissions and Network Shares

To complete the lab, I configured **file sharing and access control** on the server.  
I created shared folders, defined both **NTFS** and **share-level permissions**, and tested how different user groups interacted with those resources.

For example:
- `IT_Staff` users had full read/write access.  
- `HR_Staff` users were restricted to read-only access.

This demonstrated how layered permissions protect sensitive data while keeping workflows efficient.

---

## Outcome

By the end of this project, I had:

- Built a functioning Active Directory domain from scratch.  
- Configured DNS, DHCP, and Group Policy management.  
- Managed user accounts and security groups through ADUC.  
- Applied GPOs for security and usability.  
- Implemented file sharing with proper access control.  

Through this process, I developed not just technical skill, but a stronger sense of **how IT systems are structured, secured, and maintained** in real-world environments.

---

## Next Steps

To extend this project, I plan to:

- Automate user and GPO management using **PowerShell**.  
- Implement **event log monitoring** and alerting.  
- Test **backup and recovery** procedures for the domain controller.  

---

*This lab represents my foundational work in system administration — combining hands-on configuration, structured documentation, and professional presentation.*

