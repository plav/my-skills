---
name: maintenance-guide
description: Checklist for keeping software healthy over time. Use when dealing with tech debt, upgrading dependencies or runtimes, working in legacy code, removing dead code or features, or making the case for maintenance work.
---

# Maintenance

## Checklist
- Tech debt tracked visibly, not just complained about
- Dependencies and runtimes upgraded regularly, not in one big jump
- Dead code and unused features removed
- Tests in place before changing legacy code
- Maintenance work tied to business impact when proposing it

## Tech debt
- Deliberate (chosen, with a plan) vs accidental (discovered later)
- Pay down where it slows current work most
- Make it visible: tickets with impact and cost estimate
- Boy scout rule: leave code a little cleaner

## Upgrades
- Small, frequent upgrades are cheaper than rare large ones
- Automate with Dependabot/Renovate
- Read changelogs for breaking changes
- Watch end-of-life dates for languages and frameworks

## Legacy code
- Add characterisation tests to capture current behaviour first
- Change in small, safe steps
- Strangler pattern: replace piece by piece, not big-bang rewrite

## Removing things
- Check usage (logs, metrics) before deleting
- Deprecate with notice if others depend on it

## Lessons from my work
- Recurring manual fixes are maintenance debt: fix the cause or write an SOP
- Dependency upgrades often arrive as Snyk tickets; batch similar ones per service where possible
- Runtime upgrades (e.g. Node versions for PCI) are a chance to bundle small fixes, but keep releases decoupled if risk differs

## Further reading
- Technical debt quadrant (Martin Fowler): https://martinfowler.com/bliki/TechnicalDebtQuadrant.html
- Book: Working Effectively with Legacy Code, Michael Feathers
