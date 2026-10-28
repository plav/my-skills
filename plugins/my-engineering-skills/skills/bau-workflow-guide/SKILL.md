---
name: bau-workflow-guide
description: How my current team works day to day in BAU (support engineering). Use whenever I'm picking up, writing or updating a Jira ticket at work, writing a bug analysis, test steps, a release ticket or an SOP, preparing for CAB, or handing work to QA or Production Services. Based on patterns in my own tickets; never put customer names, credentials or personal data in anything written from it.
---

# BAU workflow (current team)

## Ticket types I work on
- Bug: something broken in production or QA
- Support Request: investigation or fix raised by another team
- Task: planned work, SOPs, security (Snyk) remediation
- Release: one per production deployment, linked to the work it ships
- Incidents (INC) and architecture stories (ARC) link in as "action item from"

## Workflow
- Backlog -> In progress -> Ready for QA -> QA in progress -> Released / Closed
- Blocked: say what it's waiting on and who owns the unblock, in a comment
- Moving to Ready for QA means test steps are written and the PR is approved

## Fields to fill in before QA
- Acceptance Criteria: The Problem / The Expected Behaviour / When BAU can consider this Done (numbered, each one testable)
- BAU - Test Steps
- Impacted repo(s), endpoint(s) and area
- PCI Impact?, Requires QA testing?, Infra config updated?
- PR Approved and Merged to Main
- SLA/OLA category and details (or why none applies)
- SOP candidate? (if Production Services could run it themselves next time)

## Bug write-up structure (what worked well)
- Impact: who is affected, how often, since when, with numbers
- Expected vs actual behaviour
- Failure chain: step-by-step from trigger to symptom, with file:line references
- Evidence: logs, timestamps, stack traces, query plans (no secrets or customer data)
- Root cause
- What needs to change: numbered, and note which items must ship together
- Also worth fixing while in the code (separate from the main fix)
- Not in scope, and who owns it instead
- How to verify
- Other information: deadlines, leading indicators to watch after release

## Test steps structure
- Prerequisites: access, tools (Postman, k9s, Datadog, browser dev tools), test data
- Numbered tests, each with expected results, mapped to AC numbers
- Known existing issues the tester might hit
- How to force failure paths (and a reminder to revert temporary changes)
- Regression checks for neighbouring features
- Unit test command and expected pass count
- Cleanup steps (and anything NOT to click)

## Security (Snyk) tickets
- Read severity, CVE, exploit maturity, fixability
- Upgrade or patch the dependency; run tests; run npm audit
- Smoke test the main endpoints of the service
- Retest in Snyk and confirm resolved; PCI findings have SLA due dates

## Release tickets
- Versions released (from -> to) for each repo
- Release steps: pre-checks, stakeholder comms, make commands or Actions workflow, env-config merged
- Pre-checks: PRs merged, versions match, no job/batch currently running
- Release window (e.g. early morning) and downtime required?
- Change / Reason for change / Impact, written for non-engineers
- Rollback version, and what behaviour comes back if rolled back
- CAB approval and release manager sign-off before the release date
- After release: watch logs and the next scheduled run

## SOPs (handover to Production Services)
- Metadata: author, approver, status, key contacts, time to run, frequency
- Description of the process and why it fails
- Key risks
- Requirements: access, accounts, alerts to subscribe to
- Step-by-step, with options if there's more than one way
- Exit criteria: how to confirm it worked
- Review history: reviewed yearly
- Use an existing approved SOP as the template

## Habits that help
- Write the analysis in the ticket, link deeper docs in the repo
- Name what must ship together so a partial fix can't make things worse
- Separate code fixes from data fixes and DBA/infra work
- Confirm env config per environment (QA must not point at production third parties)
- If a hotfix is applied directly in a console, merge the same change to git straight after
