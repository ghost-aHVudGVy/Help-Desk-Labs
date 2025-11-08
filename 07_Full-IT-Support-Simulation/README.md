# End-to-End Help Desk Simulation

This lab simulates the complete workflow of onboarding a new employee in a Windows domain environment. The goal was to walk through the same steps an IT Support specialist would perform in a real workplace, from account provisioning, workstation configuration, resource access, application setup, troubleshooting, to documentation.

---

## Scenario

A new employee joined the organization and required full IT setup:

- A domain and Microsoft 365 user account
- Workstation configuration and login access
- Access to shared folders and required permissions
- Standard software installation
- Connection to printers and network resources

I worked through this request from start to finish, documenting every step in the ticketing system as if this were an actual onboarding request.

---

## What I Did

### 1. Account Provisioning
I created the new user in **Active Directory**, assigned them to the correct **security groups**, and synchronized their account to **Microsoft 365**. Once the account appeared in the cloud, I configured licensing and verified mailbox availability.

### 2. Workstation Setup
I prepared a domain-joined workstation for the employee, confirmed Group Policy settings applied correctly, and signed in using the new credentials to validate login and profile setup.

### 3. Access to Network & Shared Resources
I assigned the user the appropriate file share permissions and mapped shared network drives. I confirmed that access aligned to least-privilege principles while still supporting the user’s role.

### 4. Application Setup
Using Group Policy and manual installation where needed, I installed the software required for the employee’s department. I verified application launch, license activation where applicable, and sign-in functionality.

### 5. Troubleshooting a Support Issue
To simulate real-world support follow-through, I resolved a user-level issue—in this case, a network printer connection failure.  
I tested printer spool services, verified network reachability, re-added the device, and printed a test page to confirm everything was functioning correctly.

### 6. Documentation and Ticket Closure
Throughout the process, I maintained a structured and concise record in the ticket:

- What was requested
- Steps taken
- Configuration changes
- Testing performed
- Final confirmation with the user

This ensured the ticket history demonstrated both technical accuracy and clear communication.

---

## Key Skills Demonstrated

- Active Directory and Microsoft 365 administration
- Workstation configuration and Group Policy troubleshooting
- Network access and resource permission management
- Standard software deployment practices
- Systematic troubleshooting and verification
- Professional support documentation and user communication

---

## What I Learned

This simulation reinforced the importance of a **methodical approach** when supporting users:

- Set up accounts and permissions carefully to avoid downstream issues
- Test each step as you go—don’t assume it works until proven
- Communicate clearly, both with users and in the documentation
- Treat every action as part of a larger workflow, not an isolated task

Working through the process end-to-end highlighted how onboarding is both technical and procedural, requiring accuracy, patience, and consistency.

---

## Summary

This project captures the real responsibilities of an IT Support professional—provisioning users, preparing systems, enabling access, resolving issues, and documenting thoroughly.  
It demonstrates the ability to manage technical tasks while maintaining a professional and organized workflow that aligns with real help desk standards.


