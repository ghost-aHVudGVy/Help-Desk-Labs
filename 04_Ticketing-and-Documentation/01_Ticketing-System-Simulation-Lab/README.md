# Ticketing-System-Simulation-Lab

This project demonstrates how I planned, built, and worked with an IT service desk environment using **Jira Service Management** and a Windows domain lab. The goal of the lab was to simulate a realistic help desk workflow — from receiving support requests, to troubleshooting, documenting the fix, and closing out tickets following standard practices.

This lab gave me hands-on experience with ticket triage, communication, workflow management, root-cause analysis, and system administration tasks across Active Directory, printers, networking, and user applications.

---

## Overview of the Lab Environment

I built a small corporate-style environment to support the ticket scenarios:

- **Domain:** `corp.local`
- **Domain Controller:** `DC01` (Active Directory, DNS, DHCP)
- **Client Workstation:** `Client01`
- **Shared Network Printer:** `\\DC01\Office_Printer`
- **User Accounts & Group Policies** configured for standard office use

This environment provided a realistic foundation for testing and resolving user support issues.

---

## Jira Service Desk Configuration

I created a dedicated Service Management project to manage IT support requests. Within Jira, I customized:

- **Request forms** to capture all relevant user information
- **Queues** for organizing incoming tickets
- **Workflows** to match real support lifecycles:
  - New → In Progress → Waiting for User → Resolved → Closed
- **Comment templates** for common support responses (e.g., password resets, VPN troubleshooting)
- **SLA targets** based on priority to simulate response expectations

This allowed the project to function similarly to a real help desk ticketing system used in professional environments.

---

## Tickets Worked & Troubleshooting Performed

I created and resolved a set of common workplace IT support tickets. Each ticket included:
- A clear problem description
- A documented troubleshooting process
- Verification steps and resolution notes

The support cases covered:

1. Password reset and account unlock
2. Network printer not responding
3. Outlook not syncing mail
4. Domain join failure on a workstation
5. VPN authentication errors
6. Slow network performance investigation
7. Post-update blue screen (BSOD) diagnosis
8. Software installation request with approval handling
9. Network drive mapping failure due to permissions
10. File access privilege change request

For each case, I reproduced the issue, applied relevant troubleshooting steps, and confirmed the fix with follow-up testing. The resolutions ranged from account and permission changes to network diagnostics, service troubleshooting, log analysis, and user communication.

---

## Key Skills Demonstrated

- Incident management and ticket workflow practices
- Clear written communication when documenting solutions
- Active Directory user and policy administration
- Printer and network resource configuration
- Basic networking and DNS troubleshooting
- Application support (Outlook, VPN, Windows services)
- Root-cause analysis based on logs and system behavior

---

## What I Learned

This project reinforced how important it is to stay methodical:
- Collect symptoms
- Confirm what changed
- Test assumptions one step at a time
- Document the reasoning behind the fix, not just the fix itself

It also improved my ability to explain technical issues in a clear and professional way — something that makes support work smoother for both users and teams.

---

## Repository Contents

This repository includes:
- Screenshots demonstrating the Jira setup, workflows, and ticket resolution stages
- Troubleshooting notes and resolution documentation

No confidential or proprietary data is included.

---

## Final Thoughts

This lab reflects the real responsibilities of an IT Support / Service Desk role. It shows my ability to manage tickets professionally, troubleshoot efficiently, and communicate clearly — all while working within structured processes.

If you'd like to discuss the project, feel free to reach out.

