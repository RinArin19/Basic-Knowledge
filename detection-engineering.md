# Detection Engineering: Writing Rules Analysts Can Trust

**Segment:** Detection. **Audience:** L2 analysts and SOC engineers. **Goal:** build detection rules that find real threats at a volume the team can handle.

A good detection rule has a clear purpose, tested logic, and an owner, because rules that nobody trusts get ignored.

## Rule lifecycle

| Stage | What to do | Output |
|---|---|---|
| Idea | Start from an attacker behavior or a past incident | A short hypothesis |
| Build | Write the logic against the right log source | A draft rule |
| Test | Run it on historical data and on simulated activity | Hit counts and sample results |
| Tune | Exclude known-benign patterns without blinding the rule | An updated rule with documented exclusions |
| Document | Write the purpose, triage steps, and escalation path | A runbook linked from the alert |
| Review | Check the quality of hits on a schedule | Keep, tune, or retire the rule |

## What every rule needs

- A name that says what it detects
- An ATT&CK technique mapping
- The data source and fields it depends on
- A severity and an expected response
- An owner and a review date
- A list of known false positives

## Measuring quality

| Metric | What it tells you |
|---|---|
| True positive rate | How often alerts turn out to be real |
| Alerts per analyst per shift | Whether the queue is manageable |
| Time to triage | Whether the alert carries enough context |
| Coverage by ATT&CK technique | Where detection gaps remain |

## Tune safely

Exclude benign activity with narrow, specific attributes, such as one service account on one host, rather than broad ones. Record why each exclusion exists, revisit it on a schedule, and test the rule again after every change.

## Common mistakes

- Shipping rules that were never tested on historical data.
- Alerts that arrive with no triage guidance.
- Never retiring rules for systems that no longer exist.
