# Device & Peripheral Support Labs

This project focuses on two core aspects of end-user and systems support in a Windows domain environment: managing shared printers through a centralized print server, and enabling secure remote access for administration and troubleshooting. Both labs were completed in a simulated enterprise network using a domain controller and a domain-joined workstation.

The goal was to demonstrate not only how to configure these services, but also how to validate functionality, document support actions, and troubleshoot issues with a structured approach.

---

## Lab 1 — Print Server Deployment & Printer Distribution

In this lab, I set up a Windows Print Server and deployed a shared network printer to a domain workstation using Group Policy. Since the environment did not include physical printers, I created a virtual printer using a Standard TCP/IP port with a simulated IP address.

After installing and configuring the Print and Document Services role, I created and shared the virtual printer, verified permissions, and confirmed manual connectivity from a client workstation. Once functionality was confirmed, I automated deployment by assigning the printer through a Group Policy Object, ensuring that users would receive the printer automatically without manual configuration.

To validate the setup, I performed a print test from the client and monitored the print queue on the server to confirm the job was processed correctly. I also reviewed service status, firewall allowances, and connectivity to ensure stability and reliability.

**Key skills demonstrated:**
- Print Server installation and configuration
- Creating and sharing network printers
- Group Policy deployment for user-level resource access
- Print spooler and driver troubleshooting

---

## Lab 2 — Remote Access & Support Tools

This lab focused on configuring and validating Remote Desktop Protocol (RDP) for administrative and support purposes across the domain. I enabled Remote Desktop on both systems, ensured appropriate firewall rules were active, and verified that Remote Desktop Services were running correctly.

Once RDP access was established, I confirmed remote connectivity by initiating remote sessions and verifying full interaction with the client system. To simulate a real support scenario, I documented a mock troubleshooting session in a support log, including the issue description, steps taken, and the resolution.

This lab demonstrated how remote support tools are configured and how support interactions are recorded to maintain clarity, accountability, and repeatability in real IT environments.

**Key skills demonstrated:**
- Enabling and securing Remote Desktop functionality
- Verifying service availability and firewall configurations
- Conducting remote support operations
- Writing structured support session documentation

---

## Outcome

Through these labs, I strengthened my understanding of managing shared resources and providing remote assistance in a Windows domain environment. The work emphasized not only configuration, but also validation, structured troubleshooting, and documentation.

---

## Additional Documentation

Each lab in this project includes more detailed, step-by-step walkthroughs along with screenshots and log files.  
If you would like to review the full process or see troubleshooting and verification steps, you can explore the individual lab folders in this repository.

