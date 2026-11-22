# Identity and Access Management: Least Privilege, MFA, and Privileged Accounts

**Segment:** Identity. **Audience:** analysts, IT admins, and managers who approve access. **Goal:** limit what a stolen account can do and keep access matched to current roles.

Attackers frequently sign in with stolen valid accounts, so limiting what each account can do shrinks the damage after a password is taken.

## Core principles

| Principle | What it means | Example |
|---|---|---|
| Least privilege | Grant only the access a role needs | A support agent can reset passwords but cannot read payroll files |
| Separation of duties | No one person controls an entire sensitive process | The person who requests a payment cannot approve it |
| Strong authentication | A second factor on every sign-in, with stronger methods for sensitive roles | An authenticator app or hardware key rather than SMS codes where possible |
| Just-in-time access | Elevated rights last a short window, then are removed | An admin role activated for two hours with an approval |

## Account types and their controls

| Account | Main risk | Controls |
|---|---|---|
| Everyday user | Phishing and password reuse | MFA, unique passwords, awareness training |
| Administrator | High impact if stolen | A separate admin account, MFA, no email or web browsing, activity logging |
| Service account | Static password and no owner | Store the secret in a vault, rotate it, restrict where it can sign in, assign an owner |
| Contractor or third party | Access outlives the contract | Expiry dates, a named sponsor, a review at contract end |

## Joiner, mover, leaver

- **Joiners:** access is requested by role and approved by the manager.
- **Movers:** old access is removed when the role changes, because access piles up over time.
- **Leavers:** accounts are disabled and sessions and tokens revoked on the same day.

## Reviews to run on a schedule

- Membership of privileged groups, reviewed quarterly.
- Dormant accounts and accounts without MFA.
- Service accounts that have no owner.

## Common mistakes

- Granting admin rights "temporarily" and never removing them.
- Sharing one account between several people.
- Resetting a password without revoking active sessions and tokens.
