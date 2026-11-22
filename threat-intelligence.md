# Threat Intelligence: Turning Indicators into Detections

**Segment:** Threat intelligence. **Audience:** analysts and threat hunters. **Goal:** use intelligence to improve detections instead of only filling a feed.

Indicators such as IP addresses go stale quickly while attacker behaviors stay useful far longer, so the best use of intelligence is to turn it into detections for behavior.

## Types of intelligence

| Type | Question it answers | Typical consumer | Example |
|---|---|---|---|
| Strategic | Who targets our industry, and why? | Leadership | A report on groups targeting the sector |
| Operational | How are current campaigns run? | SOC leads and hunters | A campaign write-up with tools and techniques |
| Tactical | Which techniques do attackers use? | Detection engineers | ATT&CK technique mappings |
| Technical | Which indicators belong to an attack? | Analysts and automation | IP addresses, domains, file hashes |

## Indicators by lifespan

| Indicator | How easily attackers change it | Detection value |
|---|---|---|
| File hashes | Trivially | Short-lived, exact matches only |
| IP addresses | Easily | Short-lived, and shared hosting causes false positives |
| Domains | With moderate effort | Useful for days to weeks |
| Tools and artifacts | With real effort | Longer-lived |
| Behaviors (ATT&CK techniques) | With the most effort | Longest-lived, and best for detection |

## From report to detection

- Read the report and pull out indicators and behaviors.
- Check relevance: do you run the targeted software or own the exposed asset?
- Search past logs for the indicators to see whether you were already affected.
- Write or update detections for the behaviors, not only the indicators.
- Record the source, a confidence level, and an expiry date for every indicator.

## Judge your sources

Ask who published the intelligence, how they know it, how recent it is, and whether other sources confirm it. Give each item a confidence level, and respect Traffic Light Protocol markings when sharing.

## Common mistakes

- Blocking indicators forever with no expiry date.
- Treating every feed as equally reliable.
- Collecting intelligence without a question it is meant to answer.
