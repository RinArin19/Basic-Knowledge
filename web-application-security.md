# Web Application Security: Reading Attacks in WAF and Application Logs

**Segment:** Application security. **Audience:** analysts moving toward AppSec, and developers. **Goal:** recognize common web attack attempts in logs and tell blocked probes from successful attacks.

A WAF log shows what was attempted, while the application and web server logs show whether it worked, so you need both to judge an incident.

## Common attack classes and what they leave behind

These classes follow the OWASP Top 10. Check the current edition of the list for exact names and ordering.

| Attack class | What the request may look like | What confirms success |
|---|---|---|
| Injection (SQL, command) | SQL keywords, quotes, or shell characters in parameters | Database errors, unusual response sizes or times, unexpected data in responses |
| Broken access control | The same endpoint requested with sequential or altered IDs | Successful responses for records the user does not own |
| Cross-site scripting | Script tags or event handlers in input fields and URLs | The payload echoed back unescaped, or stored and served later |
| Authentication attacks | Bursts of failed logins, or credential stuffing from many addresses | A success after many failures, or new sessions from unusual places |
| Server-side request forgery | Parameters containing internal addresses or cloud metadata URLs | Outbound requests from the server to those addresses |
| Path traversal | ../ sequences in file parameters | Responses containing system file content |

## Triage steps

1. Check the WAF action: blocked, allowed, or only logged.
2. Find the same request in the web server or application logs and read the response status and size.
3. Group requests by source address and user agent to separate scanners from targeted attacks.
4. Look for follow-up requests from the same source after any allowed request.
5. Escalate when a probe received a success response or sensitive data was returned.

## Signs of automated scanning

- Hundreds of paths requested within seconds, mostly returning not-found errors
- Known scanner user agents
- The same payload tried against many endpoints

## Common mistakes

- Treating every WAF block as an incident.
- Never checking whether allowed requests succeeded.
- Overlooking slow probing that is spread across many source addresses.
