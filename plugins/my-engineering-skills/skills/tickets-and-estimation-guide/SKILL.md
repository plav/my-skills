---
name: tickets-and-estimation-guide
description: Checklist for writing tickets, estimating and tracking work. Use when creating or picking up a ticket, breaking down work, estimating effort, updating progress, or flagging blockers and scope changes. See planning-and-requirements-guide for stories and acceptance criteria in depth.
---

# Tickets and estimation

## Checklist
- Clear title: what, not how
- Context: why it matters, links to designs, docs, related tickets
- Acceptance criteria
- Small enough to finish in a few days
- Estimated by the team
- Blockers and dependencies noted

## Writing tickets
- Bug: steps to reproduce, expected vs actual, environment, screenshots/logs
- Story: user, goal, reason, acceptance criteria
- Task/spike: goal, timebox, expected output

## Picking up a ticket
- Read it fully; ask questions before starting
- Check acceptance criteria are testable
- Note assumptions in the ticket

## Estimating
- Break work down until each piece is estimable
- Include testing, review, deployment, not just coding
- Unknowns: spike first, then estimate
- Ranges are more honest than single numbers

## During the work
- Keep status current
- Flag blockers the same day
- Scope grows? Raise it; split into a new ticket

## Lessons from my work
- See bau-workflow-guide for ticket types, fields and statuses used at work
- Acceptance criteria format used: The Problem / Expected Behaviour / When BAU can consider this Done
- Record why ACs changed after review, in the AC itself
- Blocked tickets: comment what you're waiting on and from whom
- Team Jira has a T-shirt size field; check whether the team actually uses it before estimating in points

## Further reading
- Agile estimation (Atlassian): https://www.atlassian.com/agile/project-management/estimation
