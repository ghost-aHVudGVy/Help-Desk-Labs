# Networking & Connectivity Labs
This project focuses on building practical troubleshooting skills in a Windows domain network. I worked with a Domain Controller (running AD DS and DNS) and a domain-joined client to first validate healthy connectivity, then intentionally break and repair network services. 

Later, I configured VPN access and recreated common failure scenarios to demonstrate structured troubleshooting.

---

## Lab 1 — Baseline Diagnostics & DNS Troubleshooting

I began by confirming normal network operations when the environment was healthy. I documented:

- Full network configuration (`ipconfig /all`)
- Connectivity to gateway and Domain Controller using `ping` and `tracert`
- DNS name resolution for internal and external hosts using `nslookup`

After establishing a baseline, I intentionally misconfigured the DNS settings on the client by pointing it to a non-existent DNS server. This resulted in failed name resolution while basic network connectivity still worked. 
To restore functionality, I reconfigured the DNS server back to the Domain Controller’s IP and flushed the DNS cache. Name resolution immediately returned to normal.

This lab reinforced how DNS issues often appear as general connectivity failures, and why verifying configuration against a known-good baseline is critical.

---

## Lab 2 — VPN Setup & Failure Scenario Testing

Next, I configured VPN access using Windows RRAS on the server and a built-in VPN client on the workstation. After connecting successfully, I verified internal resource access through the tunnel (IP routing and DNS queries).

After that to test real-world troubleshooting situations, I recreated two common VPN issues:

### Authentication Failure:
I connected with incorrect login credentials to generate an authentication error. I reviewed Event Viewer and RRAS logs to confirm the cause, then corrected the user permissions and credentials to restore access.

### DNS Resolution Failure Over VPN:
The VPN connection succeeded but internal hostnames did not resolve. The issue was traced to the VPN adapter not receiving the internal DNS server address. After modifying the RRAS configuration to provide the correct DNS IP and refreshing the client configuration, internal name resolution worked as expected.

This lab highlighted the importance of verifying both authentication and DNS configuration when diagnosing VPN issues.

---

## Key Skills Demonstrated
- Windows network troubleshooting methodology
- DNS configuration and repair
- VPN (RRAS) setup and client configuration
- Log-based root cause analysis (Event Viewer, RRAS logs)
- Clear documentation of tests and resolutions

---

## Outcome

By intentionally breaking and fixing both DNS and VPN connectivity, I developed a repeatable diagnostic approach based on baseline comparison, configuration validation, and targeted testing. This strengthened my ability to quickly identify root causes in real-world network support situations.

---

## Additional Documentation

Each lab in this project includes detailed, step-by-step walkthroughs, annotated screenshots, and captured log outputs.  
If you would like to review the full process, troubleshooting notes, or supporting evidence, you can open the individual lab folders in this repository.
