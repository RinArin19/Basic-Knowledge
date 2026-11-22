# Ransomware Readiness: Prevent, Detect, Recover

**Segment:** Ransomware. **Audience:** analysts and IT leads. **Goal:** reduce the chance of an attack, catch it early, and restore without depending on the attacker.

Ransomware readiness rests on three layers: block the common entry points, spot the early warning signs, and be able to restore your own systems.

## Three layers of defense

| Layer | Controls |
|---|---|
| Prevent | MFA on remote access and email, patching of internet-facing systems, email attachment and link filtering, restricted admin rights, network segmentation |
| Detect | EDR on all endpoints, alerts for mass file changes, alerts for backup or shadow copy deletion, monitoring of new admin accounts and unusual remote access |
| Recover | Offline or immutable backups, tested restores, a documented recovery order, an offline copy of the response plan and key contacts |

## Early warning signs

| Sign | Why it matters |
|---|---|
| Shadow copy or backup deletion commands | Attackers remove recovery options before encrypting |
| Security tools disabled or tampered with | Preparation for encryption |
| New admin accounts or unusual domain admin use | Privilege escalation |
| Large outbound transfers | Data may be stolen before encryption |
| Many files renamed or changed within minutes | Encryption may be in progress |
| Unfamiliar remote access tools | Possible persistence |

## First actions when encryption is under way

- Isolate affected hosts from the network at once. Follow your plan on powering off, because shutting down loses memory evidence.
- Disconnect backup systems and disable compromised accounts.
- Activate the incident response plan and notify management and legal.
- Preserve evidence, including the ransom note and sample encrypted files.

## Recovery planning

- Agree on a recovery order for systems, starting with the ones the business needs most.
- Test restores on a schedule and record how long they take.
- Keep the response plan and contact list somewhere that survives an outage.
- Decide in advance who may make decisions on legal and regulatory notification.

## Common mistakes

- Keeping backups on the same network with the same credentials as production.
- Never testing a restore.
- Rebuilding systems before removing the attacker's access.
