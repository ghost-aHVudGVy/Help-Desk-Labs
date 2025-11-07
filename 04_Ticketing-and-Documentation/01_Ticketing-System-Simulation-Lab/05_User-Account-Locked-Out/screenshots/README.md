# Ticket #5 — User Account Locked Out

## Issue Summary

A user reported being unable to sign into their domain account. The workstation displayed the message:

```
The referenced account is currently locked out and may not be logged on to.
```

The lockout occurred after multiple incorrect password attempts. The user had recently changed their password, which suggested that outdated credentials may still have been stored on the system, causing repeated authentication failures.

**User Message:**  
“I changed my password recently and now it keeps saying my account is locked.”

**Impact:** The user was completely unable to sign in and perform work duties.  
**Priority:** Medium

[Account-Lockout-Ticket](./01_Account-Lockout-Ticket.png)

---

## Resolution

I accessed **Active Directory Users and Computers** on **DC01** to investigate the account status. The user account showed as locked.

[User-Lockout](./02_User-Lockout.png)

The account was unlocked through the **Account** tab in the user’s properties panel.

[Unlocking-The-Account](./03_Unlocking-The-Account.png)

Since the user had recently changed their password, I checked for cached or saved credentials. On the user’s workstation, **Credential Manager** was opened and any stored credentials related to VPN, Wi-Fi, Outlook, or other network authentication services were removed to prevent repeated lockouts from outdated passwords being used automatically.

The user then logged in again using the correct password and confirmed successful access to email, network resources, and mapped drives.

---

## Outcome

The user regained access to their account and no further lockouts occurred after clearing stored credentials.

**Status:** Resolved  
**User Impact:** Account access fully restored

---

## Notes

- Repeated lockouts after a password change are commonly caused by cached credentials or background services using the old password.
- Clearing Credential Manager is an effective preventive step.
