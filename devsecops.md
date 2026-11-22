# DevSecOps: Putting Security Checks in the CI/CD Pipeline

**Segment:** DevSecOps. **Audience:** developers, AppSec engineers, and platform teams. **Goal:** catch security problems early by adding automated checks to builds and deployments.

Automated checks at each pipeline stage find problems when they are cheapest to fix, but only if the team acts on the results.

## Checks by pipeline stage

| Stage | Check | What it catches |
|---|---|---|
| Commit | Secret scanning and pre-commit hooks | Passwords, API keys, and tokens committed to code |
| Build | Dependency scanning and a software bill of materials | Known vulnerable libraries and an inventory of components |
| Test | Static analysis (SAST) and dynamic testing (DAST) on a test build | Insecure code patterns and runtime issues such as injection or missing headers |
| Package | Container image scanning and signing | Vulnerable base images and tampered artifacts |
| Deploy | Infrastructure-as-code scanning and policy checks | Public storage, open ports, and other misconfigurations |
| Run | Runtime monitoring and logging | Attacks and configuration drift after release |

## Make gates workable

- Block the build on critical, high-confidence findings and send the rest to the backlog with owners.
- Tune noisy checks and track false positives.
- Show fix guidance where developers work, such as pull request comments.
- Measure time to fix, findings per release, and the share of repositories covered.

## Protect the pipeline itself

- Use least-privilege tokens and short-lived credentials.
- Protect the main branch with required reviews and checks.
- Pin dependencies and verify them.
- Separate build permissions from deploy permissions.
- Log every change to pipeline configuration.

## Common mistakes

- Adding scanners whose reports nobody reads.
- Giving the pipeline broad admin credentials.
- Treating security as a final gate before release instead of a continuous check.
