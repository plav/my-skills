---
name: ticket-kickoff
description: Before starting work on any Jira ticket, list the skills that apply and let me pick. Use whenever I share a ticket key (e.g. RDLP-1234), a Jira link, or paste ticket content and ask for help with it, even if I don't mention skills. Runs before any other ticket work.
---

# Ticket kickoff

Pick skills with me before doing any work on a ticket.

## Steps
1. Read the ticket: type, status, description, AC, test steps, linked issues. Use the Atlassian connector if a key or link is given. Read only; change nothing.
2. In one line, say what the ticket is and what stage it's at.
3. List the skills that fit, using the routing table below. Recommended ones first, then optional ones. One short line each saying why it fits this ticket.
4. Stop and ask me to pick (e.g. "Reply with the numbers, 'all', or 'recommended'").
5. Do no ticket work until I reply. Then load only the skills I picked.

## Output format
**RDLP-XXXX** - <type>, <status>. <one-line summary>

Recommended
1. <skill> - <why, for this ticket>

Optional
3. <skill> - <why>

Which ones?

## Routing table
Always consider: bau-workflow-guide (fields, statuses, team format).

| Ticket signal | Skills |
|---|---|
| Bug, incident, failing job, root cause needed | bug-investigation-writeup, observability-and-debugging-guide |
| Moving to Ready for QA, test steps missing or weak | qa-test-steps-writer, testing-guide |
| Snyk, CVE, dependency upgrade | snyk-remediation-workflow, qa-test-steps-writer |
| Ready to release, CAB, deployment | release-ticket-writer, production-readiness-guide |
| Secrets, credentials, logging of sensitive data, auth, PCI | security-guide |
| Batch jobs, retries, queues, scheduled processes | concurrency-and-async-guide, distributed-systems-guide |
| SQL, data fixes, schema, slow queries | databases-guide, data-guide |
| SOP or handover to Production Services | bau-workflow-guide (SOP section), documentation-guide |
| Writing or changing code | how-to-work-for-me, clean-code-guide, code-review-guide |
| Vague AC or scope | planning-and-requirements-guide, tickets-and-estimation-guide |
| Slow endpoint, timeouts | performance-guide |
| Old runtime, tech debt | maintenance-guide |
| Plan or approach to stress-test | grilling |
| Writing for non-engineers | humanizer |

Only list skills that are actually available. Suggest 2-5 recommended; don't pad the list.

## Rules
- Never include customer names, credentials, account IDs or personal data in the list or summary.
- If the ticket can't be read, say so and ask me to paste it.
- Keep the whole response short.
