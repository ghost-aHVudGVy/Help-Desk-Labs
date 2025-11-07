# Ticket #1 — Password Reset Request

## Issue Summary

The user reported that they were unable to log into their workstation at the start of the workday and believed their password had expired. Since the user could not access email or shared resources, this issue directly affected productivity and required prompt attention.

**User Message:**  
“Hello, I am unable to sign into my account this morning. I believe my password has expired.”

**Impact:** The user was unable to perform work tasks.  
**Priority:** Medium

[Password-Reset-Ticket](./screenshots/01_Password-Reset-Ticket.png.png)

---

## Resolution

I first confirmed the issue by reviewing the user's account in Active Directory. The account was active and not locked, but the password had indeed expired.

To restore access, I opened **Active Directory Users and Computers** on the domain controller:

[ADUC-Console.png](./screenshots/02_ADUC-Console.png)

I navigated to the user’s organizational unit and selected the affected account:

From there, I used the **Reset Password** function. A temporary secure password was set, and the option **"User must change password at next logon"** was enabled to maintain account security:

[Reset-Password.png](./screenshots/03_Reset-Password.png)

After providing the temporary password to the user, they were able to sign in successfully and create a new password. I then confirmed that core services such as email and shared drive access were functioning normally.

---

## Outcome

The user regained access without the need for escalation or additional account adjustments. All services were confirmed operational after the password update.

**Status:** Resolved  
**User Impact:** Fully restored access

---

## Notes

- This was a standard password expiration case.
- No signs of account compromise or lockout issues.
- No further follow-up required.

