# Ticket #4 — Permission Change Request

## Issue Summary

A user requested access to the **Finance** shared folder located at `\\DC01\Finance`. The user stated that read/write access was needed to complete monthly expense reporting tasks. Access to this folder is restricted, so permission changes require validation and approval.

**User Message:**  
“I need access to the Finance share so I can prepare monthly expense reports.”

**Impact:** User was unable to perform required financial reporting duties.  
**Priority:** Medium  
**Approval:** Manager approval was verified before applying changes.

[Permission-Change-Request-Ticket](./01_Permission-Change-Request-Ticket.png)

---

## Resolution

The request was first reviewed to confirm business justification and managerial approval. Once validated, access control changes were applied.

On **DC01**, the **Finance** shared folder was opened and its sharing and NTFS permissions were reviewed to ensure consistent security configuration.

[Enable-Share.png](./02_Enable-Share.png)  
[Set-Shared-Permision](./03_Set-Shared-Permision.png)

The user was granted access by being added to the **Finance_RW** security group, which is designated for users requiring read/write privileges on the Finance share.

[Set-NTFS-Permisions](./04_Set-NTFS-Permisions.png)

After permissions were updated, the user mapped the shared folder as a network drive and confirmed that files could be opened, modified, and saved successfully.

[Mapping-Drive](./05_Mapping-Drive.png)  
[Drive-Mapped](./06_Drive-Mapped.png)

---

## Outcome

The user successfully gained access to the Finance share and confirmed the ability to read and modify required files.  
No further issues were reported.

**Status:** Resolved  
**User Impact:** Required access provided and working as expected

---

## Notes

- Access was granted only after verifying manager approval.
- Using the **Finance_RW** group maintains proper role-based permission structure.

