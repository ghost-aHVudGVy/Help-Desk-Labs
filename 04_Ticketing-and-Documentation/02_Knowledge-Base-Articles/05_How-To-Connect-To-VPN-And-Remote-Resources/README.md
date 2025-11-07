# Knowledge Base Article: How to Connect to VPN and Remote Resources

**Category:** Networking & Remote Access  
**Audience:** All employees  
**Last Updated:** 2025-11-07  
**Author:** Antonio Karadenizov

---

## Overview

This article provides step-by-step instructions for connecting to the corporate network remotely using a VPN. It ensures secure access to internal resources, network drives, and applications from offsite locations.

---

## Connecting to VPN (Windows)

1. Open **Settings** → **Network & Internet** → **VPN**.  
2. Click **Add a VPN connection**.  
3. Fill in the following fields:  
   - **VPN provider:** Windows (built-in)  
   - **Connection name:** Corporate VPN  
   - **Server name or address:** [Provided by IT]  
   - **VPN type:** Automatic or as specified by IT  
   - **Type of sign-in info:** Username and password  
4. Enter your **corporate credentials**.  
5. Click **Save**.  
6. Select the VPN connection and click **Connect**.  
7. Once connected, verify by accessing **internal resources** like network drives or intranet sites.

---

## Troubleshooting VPN Connection Issues

| Issue | Possible Cause | Solution |
|-------|----------------|---------|
| **Cannot connect to VPN** | Network connectivity or incorrect credentials | Verify internet connection, re-enter username and password. |
| **Authentication failed** | MFA required or expired credentials | Complete multi-factor authentication or reset password. |
| **Limited access to resources** | DNS or routing issues | Disconnect and reconnect VPN, check DNS settings. |
| **VPN disconnects frequently** | Poor internet connection or VPN timeout | Use a stable network, or adjust timeout settings in VPN client. |

---

## Accessing Remote Resources After VPN Connection

1. Open **File Explorer** and navigate to network drives (e.g., `\\ServerName\SharedFolder`).  
2. Access internal applications via **web portal or internal URLs**.  
3. For remote desktops, use **RDP** (`mstsc`) with the host name or IP address.  
4. Ensure **corporate antivirus and firewall settings** are active during remote access.  

---

## Notes

- Always connect to VPN using **corporate-approved clients**.  
- Disconnect from VPN when not actively working to conserve bandwidth.  
- Document recurring connection issues in the **ticketing system** for IT support follow-up.  
- Maintain **strong passwords and MFA** to protect remote access.  

---

**End of Article**
