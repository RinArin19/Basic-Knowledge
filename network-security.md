# Network Security: Segmentation, Firewall Rules, and Traffic Baselines

**Segment:** Network. **Audience:** L1 to L2 analysts and IT staff. **Goal:** explain how segmentation limits damage and how to spot traffic that breaks the normal pattern.

Splitting a network into zones with explicit rules between them turns one compromised device into a contained problem instead of a company-wide incident.

## Why segmentation matters

On a flat network any device can reach any other, so an attacker who lands on one laptop can scan and move to servers freely. Zones with firewall rules force the attacker to cross controls that you can log and monitor.

## Typical zones

| Zone | What it holds | Default rule |
|---|---|---|
| Users | Employee laptops and phones | Internet and approved apps only, no access to server admin ports |
| Servers | Application and database servers | Accept only the ports each application needs |
| Management | Admin workstations, jump hosts, network gear | Reachable only from approved admin devices |
| Guest and IoT | Visitors, printers, cameras, smart devices | Internet only, no route to internal zones |

## Firewall rule hygiene

- Start from deny and allow only what is documented.
- Give every rule an owner, a purpose, and a review date.
- Remove "any to any" rules and rules that no traffic has matched during the review period.
- Log denied traffic between zones, because it is often the first sign of scanning.

## Build a traffic baseline

Record what normal looks like: which hosts talk to which, on what ports, at what hours, and in what volumes. Firewall, DNS, and NetFlow logs are the usual sources. Without a baseline, every odd connection looks the same.

## Traffic worth investigating

| Pattern | Why it matters |
|---|---|
| A workstation connecting to many internal hosts on one port | Possible internal scanning or lateral movement |
| A large outbound transfer at an unusual hour | Possible data exfiltration |
| Regular, evenly spaced connections to one external address | Possible beaconing to a command-and-control server |
| RDP, SSH, or SMB between zones that never used them | Possible lateral movement |
| Many DNS lookups for random-looking names | Possible malware generating domains |

## Common mistakes

- Treating the internal network as trusted.
- Segmenting once and never reviewing the rules.
- Collecting logs but never building a baseline from them.
