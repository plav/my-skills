---
name: release-ticket-writer
description: Drafts a production release ticket ready for CAB, in my team's format. Use whenever I'm preparing a release, raising a Release ticket in Jira, writing release steps, rollback notes, or the Change / Reason for change / Impact summary, or bundling several tickets into one deployment.
---

# Release ticket writer

## Workflow
1. Gather: linked tickets, repos and versions (from -> to), PRs merged, config changes, test evidence.
2. Check the pre-release list below and flag anything missing.
3. Draft the ticket using the template.
4. If several changes are bundled, list each and say whether they could be decoupled to reduce risk.
5. Finish with a list of what I still need (CAB date, sign-off, comms, versions to confirm).

## Pre-release checks
- All PRs approved and merged to main; build versions match the ticket
- Env-config / infra config changes merged
- QA passed (link evidence)
- No scheduled job or batch running during the release window
- Affected teams told about the window and any downtime
- Rollback version known and tested if possible
- Monitoring plan for after release

## Template
**Summary**: Release: <what> (<repo> <version>, ...) - <linked tickets>
**Versions released**: <repo> <from> -> <to>
**Release window / downtime required**:
**Release steps**
1. Pre-checks (above)
2. Deploy: <make command or Actions workflow - confirm exact names>
3. Post-deploy checks: pods healthy, no new errors in logs, key endpoint returns expected response
**Rollback**: redeploy <previous versions>; note what old behaviour returns
**Change**: what is different, in plain language
**Reason for change**: the problem it solves, with evidence
**Impact**: what users/teams will notice; what does not change
**Acceptance criteria**: deployed in window; services healthy; specific behaviour confirmed; rollback available
**Business impact** (for CAB)
**Technical notes**: key code changes, timeouts/config, tests run, known issues not fixed, follow-ups
**After release**: what to watch, who with, and when (e.g. next scheduled run)

## Rules
- No credentials, account IDs or customer data in the ticket.
- Don't invent versions, commands or dates; leave <confirm> placeholders.
- Write Change / Reason / Impact so a non-engineer on CAB understands it.
