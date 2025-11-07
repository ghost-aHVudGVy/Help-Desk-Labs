# Ticket #4 — Domain Join Failure

## Issue Summary

A new workstation was unable to join the **corp.local** domain. The user confirmed that the device was connected to the network, but the system displayed the following error when attempting to join the domain:

```
The specified domain either does not exist or could not be contacted.
```

This prevented the system from being registered in Active Directory and assigned the appropriate group policies and access.

**User Message:**  
“I’m trying to join this new workstation to the domain, but it keeps saying it can’t contact the domain.”

**Impact:** The workstation could not be deployed for use.  
**Priority:** High

![Domain Join Failure Ticket](./screenshots/01_Domain-Join-Failure-Ticket.png)

---

## Resolution

I began by verifying network connectivity, which was functioning correctly. However, upon checking the network adapter configuration, the workstation was using a public DNS server rather than the internal domain controller’s DNS service.

To resolve this, the preferred DNS server on the workstation was updated to point to the domain controller at **192.168.10.10**.

![DNS Configuration](./screenshots/02_DNS-Config.png)

After updating DNS, the workstation was reattempted to be joined to the domain through the system settings:

**System → Rename this PC (Advanced) → Domain: `corp.local`**

The domain join request completed successfully.

![Successful Domain Join](./screenshots/03_Domain-Join.png)

The workstation was then rebooted, and the computer object was confirmed to be visible in **Active Directory Users and Computers**.

---

## Outcome

The workstation successfully joined the domain and was ready for user assignment.  
No further network or account issues were identified.

**Status:** Resolved  
**User Impact:** Workstation successfully deployed

---

## Notes

- Root cause was incorrect DNS configuration pointing to an external resolver.
- Internal DNS is required for domain discovery and authentication.

