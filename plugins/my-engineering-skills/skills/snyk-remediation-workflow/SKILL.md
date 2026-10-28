---
name: snyk-remediation-workflow
description: Step-by-step workflow for fixing Snyk (or npm audit) dependency vulnerabilities and writing up the ticket. Use whenever I pick up a SNYK / BAU security ticket, see a CVE or CWE in a Jira ticket, need to upgrade a vulnerable package, or write test steps for a dependency upgrade, especially for PCI-scoped services.
---

# Snyk remediation workflow

## 1. Understand the finding
- Package, vulnerable version, fixed version, CVE/CWE
- Severity, exploit maturity, fixability, SLA due date (PCI findings are stricter)
- Direct or transitive dependency? (`npm ls <package>`)
- Is the vulnerable code path actually used? Note it, but still fix by the due date

## 2. Choose the fix
- Direct dependency: upgrade to the lowest fixed version first
- Transitive: upgrade the parent package; if not possible, use an `overrides` entry in package.json and note why
- Major version jump: read the changelog for breaking changes
- No fix available: document mitigation and raise with SecOps; don't silently ignore

## 3. Make the change
- Update package.json and the lockfile together (`npm install`); commit both
- Keep the PR to the security fix only
- Check the Dockerfile/CI install command uses the lockfile as expected

## 4. Verify
- `npm test` - all suites pass
- `npm audit` - the targeted finding is gone; note any others separately
- Run the service and smoke test its main endpoints
- Check application logs for new errors
- Retest the project in Snyk and confirm the finding shows as resolved

## 5. Ticket write-up
**Acceptance criteria**: finding remediated and retested in Snyk as resolved; tests pass; main endpoints behave as before
**Test steps** (use qa-test-steps-writer):
- Authenticate as needed and call each main endpoint; expected status and response shape
- Review logs for the calls
- `npm test`: expected <n> suites / <n> tests pass
- `npm audit`: targeted vulnerability no longer reported
- Snyk retest: finding resolved
**Notes**: old -> new versions, direct/transitive, overrides used, anything not fixed and why

## Batch tip
- Several findings in the same service: fix together in one PR if low risk
- Same package across services: fix one, then repeat the pattern
