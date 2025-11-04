# VPN Configuration & Connectivity Troubleshooting Lab

The goal with this lab was not just to configure a working VPN, but also to recreate the kinds of problems end-users frequently encounter and practice resolving them effectively.

---

## Objective

- Configure VPN access using Windows Server Remote Access (RRAS).
- Connect a Windows client to the VPN using built-in tools.
- Verify internal resource access over the VPN tunnel.
- Simulate failed VPN connection scenarios to practice troubleshooting and documentation.

---

## Environment Overview

By the start of this lab, the following environment was already set up and running:

| Component | Hostname | Role | IP Address | Description |
|------------|-----------|------|-------------|--------------|
| **DC01** | `DC01` | Domain Controller | 192.168.10.10 | Active Directory Domain Services, DNS, DHCP |
| **Client01** | `Client01` | Workstation | DHCP | Domain-joined Windows 10 client |
| **Internal Network** | `LabNet` | Virtual Network | 192.168.10.0/24 | Isolated internal network used for domain communication |

This setup replicates a small corporate environment, with both machines connected through an isolated internal network to simulate a real enterprise domain.

---

## 1. Configuring VPN Services on the Server

I began by installing the **Remote Access** role and enabling **Routing and Remote Access (RRAS)**.  
During configuration, I selected **VPN access** and ensured that client IP assignment was handled inside the private network range.

**Screenshots:**
- [Remote-Access](./screenshots/01_Remote-Access.png)
- [DirectAccess-&-VPN+Routing](./screenshots/02_DirectAccess-&-VPN+Routing.png)
- [RRAS-VPN-Setup](./screenshots/03_RRAS-VPN-Setup.png)
- [RRAS-Console-Installed](./screenshots/04_RRAS-Console-Installed.png)

### Enabling User Access  
I confirmed that the test user account had **Dial-in permissions** enabled in Active Directory.  
This step is a common cause of *Error 691* authentication failures.

[Allowing-Dial-in-To-Users](./screenshots/05_Allowing-Dial-in-To-Users.png)

### Firewall Considerations  
To allow VPN traffic to reach the server, I ensured that PPTP (TCP/1723) and GRE (Protocol 47) were permitted through the firewall.

---

## 2. Configuring the VPN Client

On the Windows client, I added a new VPN profile using Windows’ built-in VPN tool.  
I pointed the configuration to the server’s internal IP address and selected username/password authentication.

[VPN-Client-Configuration](./screenshots/06_VPN-Client-Configuration.png)

---

## 3. Testing the Connection

Once connected, I verified that:

- The VPN session was established successfully.
- The client received a correct internal IP.
- Internal resources (e.g., the domain controller) were reachable.
- DNS name resolution worked through the VPN interface.

If any test failed, I logged the result for diagnosis.

[Successful-VPN-Connection](./screenshots/09_Successful-VPN-Connection.png)

---

## 4. Simulating Real User Issues

To make the lab realistic, I intentionally introduced failure conditions.

### A. Incorrect Credentials (Authentication Failure)

I attempted to connect with an incorrect password.  
The VPN client displayed an authentication error, and on the server side, logs helped confirm the root cause.

- [VPN-Connect-Failure](./screenshots/07_VPN-Connect-Failure.png)
- [VPN-Auth-log](./screenshots/08_VPN-Auth-log.png)

The issue was caused by incorrect credentials being used during authentication. 
I resolved it by verifying the user account in Active Directory, enabling Dial-in access, and reconnecting with the correct password.

### B. DNS Resolution Failure

To simulate a DNS resolution issue, I changed the DNS settings so the VPN client no longer received the internal DNS server. This caused hostnames to fail even though the VPN tunnel was active. 

I resolved it by configuring RRAS to assign the correct internal DNS (192.168.10.10) to VPN clients, then flushing the DNS cache on Client01.

---

## Key Skills Demonstrated

- Configuring RRAS and VPN services on Windows Server
- Managing user dial-in permissions and authentication policies
- Windows client VPN configuration and credential handling
- Diagnosing and resolving VPN connectivity failures
- Reading and interpreting Server Event Viewer and RRAS logs
- Network testing using: `ping`, `nslookup`, `tracert`, `Test-NetConnection`

---

## Conclusion

This lab strengthened my ability to support remote workers and diagnose real-world VPN connectivity issues. I gained hands-on experience in configuring secure access, validating internal connectivity, analyzing authentication failures, and documenting support resolutions clearly. These skills directly apply to service desk and system administration positions where secure remote access and troubleshooting are everyday responsibilities.

