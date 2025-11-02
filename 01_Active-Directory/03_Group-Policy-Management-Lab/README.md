# Group Policy Management Lab — Active Directory Environment
 
My goal with this lab was to strengthen my understanding of **Group Policy Management**, how it’s created, linked, and applied across a domain environment. I focused on practical examples that directly mirror real IT admin work, such as enforcing password policies, mapping shared drives, and standardizing user desktops.

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

## Step 1 — Creating and Linking a Desktop Wallpaper GPO

I started by logging into **DC01** as `corp\Administrator` and opening the **Group Policy Management Console (GPMC)** from Server Manager. To validate that new policies would apply correctly, I created a GPO to set a domain-wide desktop wallpaper.  
In **GPMC**, I right-clicked the domain (`corp.local`) → **Create a GPO in this domain, and Link it here…**, naming it **“Corp Desktop Wallpaper.”**

After that, I edited the GPO by enabled the setting and pointed it to a shared image on the domain controller: 

`\\DC01\Shared\wallpaper.jpg`

[GPO-Created](./screenshots/01_GPO-Created.png)
[Permissions-For-Wallpaper](./screenshots/02_Permissions-For-Wallpaper.png)
[Wallpaper-Location-Setup](./screenshots/03_Wallpaper-Location-Setup.png)
[Wallpeper-Enabled](./screenshots/04_Wallpeper-Enabled.png)

*Purpose:* Demonstrates GPO deployment that affects the user environment, confirming end-to-end policy delivery.

---

## Step 3 — Implementing a Password Policy

Next, I focused on security.  
Using the **Default Domain Policy**, I configured a password policy to enforce stronger credentials and expiration rules.

Path used:
`Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy`

I applied the following settings:
- Minimum password length: **8 characters**
- Password must meet complexity requirements: **Enabled**
- Maximum password age: **60 days**

[Password-Policy](./Lab/screenshots/05_Password-Policy.png)

*Purpose:* Shows understanding of enforcing organization-wide security standards through GPOs.

---

## Step 4 — Configure and Test Mapped Network Drives via GPO  

On **DC01**, I created a shared folder located at `C:\Shared` and shared it as `\\DC01\Shared`.  
Both **NTFS** and **Share** permissions were configured to give **Authenticated Users** read access.  

In **Group Policy Management**, I then created a new GPO called **“Corp Network Drives”** and linked it to the domain.  
Within the GPO, under  
`User Configuration → Preferences → Windows Settings → Drive Maps → New → Mapped Drive`,
I specified the following:  
- **Location:** `\\DC01\Shared`  
- **Drive Letter:** `Z:`  
- **Action:** Update  

After applying the GPO, I logged into **Client01** as the domain user `corp\jsmith` and ran:  
`gpupdate /force`

Once the policy was updated, the **Z:** drive appeared automatically in File Explorer, mapped to the shared folder on DC01.  
This confirmed that the GPO was applied successfully.  

[Share-Drive](.Lab/screenshots/06_Share-Drive.png)
[Shared-Permissions](./screenshots/07_Shared-Permissions.png)
[GPO-Mapping](./screenshots/08_GPO-Mapping.png)
[GPO-Mapping-Finished](./09_GPO-Mapping-Finished.png))
[GPUpdate-Force](./screenshots/10_GPUpdate-Force.png)
[GPO-Mapping-Result](./screenshots/11_GPO-Mapping-Result.png)

*Purpose:* Automate and verify network drive mapping for domain users through Group Policy. 

---

## Conclusion

By the end of this lab, I had successfully:

- Created and linked multiple GPOs across a domain environment.  
- Implemented both **security policies** and **user experience configurations**.  
- Verified GPO functionality on client systems in a realistic setup.

This project helped solidify my understanding of how Group Policy works within Active Directory. From design and implementation to troubleshooting and validation.  
