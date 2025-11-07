# Knowledge Base Article: How to Install a Printer

**Category:** Device & Peripheral Support  
**Audience:** All employees  
**Last Updated:** 2025-11-07  
**Author:** Antonio Karadenizov

---

## Overview

This article provides step-by-step instructions for installing a printer on a Windows workstation. It covers both **network printers** and **local printers**, ensuring users can print reliably. Troubleshooting tips are included for common printer issues.

---

## Installing a Network Printer (Windows)

1. Open **Settings** by pressing **Win + I**.  
2. Navigate to **Devices → Printers & scanners**.  
3. Click **Add a printer or scanner**.  
4. Wait for Windows to detect available network printers.  
5. Select your printer from the list and click **Add device**.  
6. If the printer is not listed, click **The printer that I want isn’t listed**, then:  
   - Choose **Add a printer using TCP/IP address or hostname**  
   - Enter the **printer IP address** or **hostname**  
   - Click **Next** and follow prompts to install the driver.  
7. After installation, print a **test page** to confirm connectivity.

---

## Installing a Local Printer (USB)

1. Connect the printer to your workstation using a **USB cable**.  
2. Power on the printer.  
3. Windows should automatically detect and install the printer driver.  
4. If prompted, follow the **on-screen instructions** to complete installation.  
5. Open **Printers & scanners** to verify the printer is listed.  
6. Print a **test page** to confirm functionality.

---

## Installing a Printer via Group Policy (GPO)

1. Open **Group Policy Management** on the server.  
2. Navigate to the relevant **Organizational Unit (OU)**.  
3. Right-click the OU and select **Create a GPO in this domain, and Link it here**.  
4. Name the GPO (e.g., "Network Printers Deployment").  
5. Edit the GPO:  
   - Navigate to **User Configuration → Preferences → Control Panel Settings → Printers**  
   - Right-click **Printers** → **New → Shared Printer**  
   - Enter the printer share path (e.g., `\\ServerName\PrinterName`)  
6. Apply the GPO and ensure users receive the update by running **gpupdate /force** on client machines.

---

## Common Issues & Troubleshooting

| Issue | Possible Cause | Solution |
|-------|----------------|---------|
| **Printer not detected** | Printer is offline or not connected | Check power, cable, and network connection. |
| **Unable to print test page** | Incorrect driver or permissions | Reinstall printer driver or verify user permissions on the printer share. |
| **Spooler service errors** | Print spooler service stopped | Restart the **Print Spooler** service in **Services.msc**. |
| **Printer appears offline** | Network connectivity issues | Ensure the printer is on the correct subnet and reachable via ping. |

---

## Notes

- Always ensure the printer driver is **compatible with your Windows version**.  
- Network printers require proper **permissions** for read/write access.  
- For persistent issues, document the problem and escalate to IT support.  
- Test printing from multiple applications to confirm full functionality.  

---

**End of Article**
