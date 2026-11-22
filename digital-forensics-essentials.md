# Digital Forensics Essentials: Evidence Handling and Order of Volatility

**Segment:** Forensics. **Audience:** L2 analysts and incident responders. **Goal:** collect evidence so that it stays intact and usable.

Evidence disappears in order of how fragile it is, so collect the most volatile data first and record every step you take.

## Order of volatility

| Priority | Source | Why it is fragile |
|---|---|---|
| First | Memory (RAM) and CPU state | Lost at shutdown or reboot |
| Next | Running processes, network connections, logged-in users | Changes from second to second |
| Then | Disk contents and file system timestamps | Changes as the system keeps running |
| Later | Remote logs, backups, and archives | Lasts longer but can rotate or expire |

## Handling evidence

- Work on copies. Image the original storage with a write blocker where possible, and hash it before and after.
- Record who handled what, when, and where, for every item.
- Note the system clock and time zone against a trusted clock.
- Store evidence in a secured location with access logging.
- Avoid installing tools on the affected system. Use trusted tools from external media.

## Chain of custody record

| Field | Example content |
|---|---|
| Item | Laptop, with its serial number |
| Collected by | The analyst's name |
| Date and time | With the time zone |
| Location | Where it was collected |
| Hash | SHA-256 of the forensic image |
| Transfers | Each handover, with name, date, and reason |

## Build a timeline

Combine file system timestamps, logs, and EDR events into one timeline sorted in UTC. Note clock differences between systems and any gaps in the data, since a missing hour can matter as much as a visible event.

## Common mistakes

- Rebooting a system before capturing memory.
- Working on the original evidence instead of a copy.
- Merging logs without converting time zones.
- Not involving legal when the case may reach law enforcement or a lawsuit.
