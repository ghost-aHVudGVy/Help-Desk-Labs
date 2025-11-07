# Knowledge Base Article: How to Map a Network Drive

**Category:** File Access & Network Shares  
**Audience:** All employees  
**Last Updated:** 2025-11-07  
**Author:** Antonio Karadenizov

---

## Overview

This article provides **detailed instructions** for connecting to a **shared network folder** on a **Windows workstation**. Mapping a **network drive** allows **quick access** to **shared files** and ensures a **persistent connection** across **reboots**. **Troubleshooting tips** are included for **common issues** such as **incorrect credentials** or **unavailable network paths**.

---

## Mapping a Network Drive via GUI

1. Open **File Explorer**.  
2. Click **This PC** in the **left-hand navigation pane**.  
3. Click the **Computer** tab at the top, then select **Map network drive**.  
4. In the **Drive** dropdown, select an **available letter** (e.g., `Z:`).  
5. In the **Folder** field, enter the **network path** using either:  
   - **UNC path:** `\\ServerName\SharedFolder`  
   - Or **browse** to locate the **shared folder**.  
6. Check **Reconnect at sign-in** to maintain the **connection** after **restarting** your **computer**.  
7. Check **Connect using different credentials** if your **login** differs from the one used for the **shared folder**.  
8. Click **Finish**.  
9. Enter your **domain credentials** when prompted.  
10. Verify the **drive** appears in **This PC** and **test** by opening the **folder**.

---

## Mapping a Network Drive via Command Prompt (Optional)

For **advanced users** or **automation purposes**, you can map a **drive** using the **command prompt**:
```cmd
net use Z: \\ServerName\SharedFolder /persistent:yes
```
- Replace `Z:` with your desired **drive letter**.

- Replace `\\ServerName\SharedFolder` with the actual **network path**.  

- `/persistent:yes` ensures the **drive reconnects** at every **login**.  

---

## Common Issues & Troubleshooting

| Issue | Possible Cause | Solution |
|-------|----------------|---------|
| **Cannot access network path** | Folder path is incorrect or server offline | Verify the path and check **network connectivity**. |
| **Access denied** | Insufficient permissions | Contact **IT** to confirm you have **read/write access**. |
| **Drive disconnects after reboot** | “Reconnect at sign-in” not selected or credentials not saved | Re-map the **drive** and ensure **Reconnect at sign-in** is checked. |
| **Repeated credential prompts** | Stored credentials mismatch | Remove old **credentials** via **Control Panel → Credential Manager** and re-enter the correct **login**. |

---

## Notes

- Always use the **UNC path** (`\\ServerName\SharedFolder`) for **consistent access**.  
- Mapping **drives** ensures **compatibility** across applications such as **Excel, Teams, and Outlook**.  
- Ensure **VPN** is active if accessing **shared drives remotely**.  
- Document any **recurring issues** in the **ticketing system** for **IT support tracking**.  

---

**End of Article**
