# Cloud Security: Shared Responsibility and Common Misconfigurations

**Segment:** Cloud. **Audience:** analysts and engineers new to cloud environments. **Goal:** know which security tasks stay with you in the cloud and which settings to check first.

Cloud providers secure the underlying infrastructure, but you remain responsible for identities, data, and configuration, which is where many cloud incidents begin.

## Shared responsibility

The split shifts as you move toward managed services, so confirm it for each service you use.

| Layer | Who secures it |
|---|---|
| Physical data centers and hardware | Provider |
| Hypervisor and managed platform services | Provider |
| Operating system and software on virtual machines | You |
| Identities, roles, and keys | You |
| Data classification and storage permissions | You |
| Network rules and public exposure | You |
| Logging, alerting, and response | You |

## Misconfigurations to check first

| Misconfiguration | Risk | What to check |
|---|---|---|
| Public storage buckets | Data exposure | Block public access by default and review bucket policies |
| Overly broad roles | A single stolen account has wide impact | Remove wildcard permissions and unused roles |
| Long-lived access keys | A leaked key gives lasting access | Prefer short-lived credentials, and rotate or delete old keys |
| Open management ports | Brute force and exploitation | Restrict SSH and RDP to a VPN or bastion host |
| Logging disabled | No evidence during an incident | Enable audit logs everywhere and send them to a protected account |
| No MFA on the root or owner account | Full account takeover | Enforce MFA and avoid daily use of the root account |

## Logs to collect

- Control-plane audit logs, which show who changed what
- Network flow logs
- Storage access logs
- Identity provider sign-in logs

## Alerts worth having

- Root or owner account sign-in
- New access key creation
- A storage bucket made public
- Logging disabled or changed
- Activity in regions you do not use

## Common mistakes

- Assuming the provider handles configuration.
- Copying production data into unprotected test environments.
- Turning logs on but never alerting on them.
