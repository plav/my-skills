---
name: production-readiness-guide
description: Checklist for shipping and running software safely in production. Use before launching a new service or major feature, when setting up alerts, health checks or backups, planning a risky deploy, or handling an incident and postmortem.
---

# Production readiness

## Checklist
- Health and readiness checks
- Graceful shutdown (finish in-flight work)
- Alerts on user-facing problems, routed to someone who can act
- Dashboards for the four golden signals
- Rollback plan tested
- Backups exist AND restores are tested
- Runbook for common issues
- Load tested in proportion to risk

## Four golden signals
- Latency, traffic, errors, saturation

## SLIs and SLOs
- SLI: what you measure (e.g. % successful requests)
- SLO: target (e.g. 99.9% over 30 days)
- Error budget: how much failure is acceptable; spend it on releasing faster

## Safe deployments
- Small changes, feature flags, canary releases
- Watch metrics after deploy; roll back fast if worse

## Backups and recovery
- RPO: how much data can we lose? RTO: how long can we be down?
- Practise restores

## Incidents
- Mitigate first (roll back, disable feature), investigate later
- One person coordinating; regular status updates
- Blameless postmortem: what happened, why, what we'll change

## Lessons from my work
- Release ticket with versions, steps, rollback version, downtime and comms; CAB approval first
- Tell affected teams not to trigger jobs during the release window
- Rollback notes should say what old behaviour comes back
- After release, watch logs and the next scheduled run, ideally with the business owner
- Set up alerts on "batch completed with failures" so failures reach the people who act on them
- Turn repeat manual fixes into SOPs for Production Services

## Further reading
- Google SRE book: https://sre.google/sre-book/table-of-contents/
- Monitoring distributed systems (golden signals): https://sre.google/sre-book/monitoring-distributed-systems/
