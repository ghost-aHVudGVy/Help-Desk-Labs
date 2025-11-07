# Ticket #2 — Printer Showing as Offline

## Issue Summary

A user reported that the shared office printer **\\DC01\Office_Printer** was showing as *Offline* on their workstation. The user attempted restarting their PC, but the issue persisted. Since printing was required for day-to-day tasks, this issue directly impacted productivity.

**User Message:**  
“The printer is showing offline. I restarted my PC but it’s still not working.”

**Impact:** The user was unable to print necessary documents.  
**Priority:** Medium

[Printer-Offline-Ticket](./screenshots/01_Printer-Offline-Ticket.png)

---

## Resolution

The issue was first verified at the user’s workstation. The printer was present, but the print spooler service was not functioning correctly.  
The **Print Spooler** service was restarted through **Services.msc**, restoring communication between the workstation and the print system.

[Restarting-Print-Queue](./screenshots/02_Restarting-Print-Queue.png)

Next, the offline printer was removed from **Devices and Printers**, and then reconnected using the shared path:

```
\\DC01\Office_Printer
```

On the domain controller (**DC01**), **Print Management** was used to clear the print queue to ensure there were no stuck print jobs causing the issue.

[Print-Queue-Cleared](./screenshots/03_Print-Queue-Cleared.png)

A test page was printed from the user’s workstation to confirm normal operation.

---

## Outcome

The printer was successfully restored and confirmed functional.  
The user was able to continue work without further issues.

**Status:** Resolved  
**User Impact:** Printing functionality fully restored

---

## Notes

- The root cause was a stalled **Print Spooler** service on the client system.
- No hardware or network faults were identified.

