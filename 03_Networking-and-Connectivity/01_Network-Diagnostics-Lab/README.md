# Network Diagnostics & Troubleshooting Lab
This lab focused on strengthening my ability to diagnose and resolve network connectivity issues in a Windows Server environment. 

The main goal was to simulate realistic Help Desk scenarios, verifying connectivity, identifying DNS misconfigurations, and documenting the troubleshooting process in a structured and professional way.

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

## 1. Baseline Network Diagnostics

I began by establishing a healthy network baseline from **Client01** to confirm that communication with the domain controller and external sites was functioning as expected.

### Step 1 — Check IP Configuration
Using PowerShell, I ran `ipconfig /all` to review the network adapter settings, DNS configuration, and gateway details.  
This provided the baseline for further connectivity checks.

[ipconfig-all](./screenshots/01_ipconfig-all.png)

---

### Step 2 — Test Connectivity
Next, I verified communication with the domain controller (`DC01`) using `ping`.  
All responses returned successfully, confirming domain reachability.

[ping-DC01](./screenshots/02_ping-DC01.png)

---

### Step 3 — Verify DNS Resolution
I tested the internal name resolution using `nslookup dc01`.  
The query returned valid results, confirming that DNS services were functioning correctly.

[nslookup-valid](./screenshots/03_nslookup-valid.png)

---

### Step 4 — Trace Network Route
To visualize the communication path between **Client01** and **DC01**, I used `tracert`.  
The results confirmed that packets were routed directly through the expected gateway with no interruptions.

[tracert-example](./screenshots/04_tracert-example.png)

---

### Step 5 — Export Diagnostic Log
To consolidate the test results, I automated the output collection into a single log file:

```powershell
(
  "=== ipconfig ===", (ipconfig /all),
  "=== ping gateway ===", (ping 192.168.10.1 -n 4),
  "=== ping DC01 ===", (ping 192.168.10.10 -n 4),
  "=== nslookup dc01 ===", (nslookup dc01),
  "=== tracert DC01 ===", (tracert 192.168.10.10)
) | Out-File C:\lab_logs\network_checks.txt
```
[network_checks](./logs/network_checks.txt)

This log provided a full record of the healthy network state for comparison later in the troubleshooting process.

---

## 2. Simulating a DNS Misconfiguration

To simulate a realistic user issue, I intentionally misconfigured the DNS server on **Client01** by setting it to an invalid address (`1.2.3.4`).
Immediately after this change, name resolution failed — a common cause of “no internet” or “can’t connect to server” tickets.

---

### Step 1 — Attempt DNS Resolution with Invalid DNS
Testing `nslookup dc01` after applying the wrong DNS server produced an error, confirming the issue.

[nslookup-bad-dns](./screenshots/05_nslookup-bad-dns.png)

---

### Step 2 — Verify Incorrect DNS Setting
I ran `Get-DnsClientServerAddress` to confirm that the adapter was indeed using the invalid DNS configuration.

[incorrect-dns](./screenshots//screenshots/06_incorrect-dns.png)

---

### Step 3 — Fix the DNS Configuration
I restored the correct DNS server address, flushed the DNS cache, and retested connectivity:

```powershell
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses 192.168.10.10
ipconfig /flushdns
nslookup dc01
ping dc01
```
Once corrected, DNS resolution and connectivity were fully restored.

[dns-fixed](./screenshots/07_dns-fixed.png)

---

### Step 4 — Document the Support Case

To simulate a real-world IT workflow, I documented the issue and resolution in a short support note.  
```
Issue: DNS server misconfigured (1.2.3.4)
Action: Restored to 192.168.10.10, flushed cache
Result: Name resolution restored
```

---

## 3. Key Takeaways

This lab was a practical exercise in **methodical network troubleshooting**, applying foundational tools like `ping`, `ipconfig`, `tracert`, and `nslookup` to identify and resolve connectivity problems.

**What I practiced:**
- Diagnosing network and DNS issues step-by-step  
- Verifying each assumption through hands-on command-line testing  
- Keeping detailed, structured documentation of every action taken  

By the end of this lab, I had a complete diagnostic log, a clear record of the simulated DNS failure.

