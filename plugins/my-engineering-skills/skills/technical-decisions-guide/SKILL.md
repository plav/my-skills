---
name: technical-decisions-guide
description: Framework for making and recording technical decisions. Use when choosing between technologies, libraries or designs, writing a technical proposal or ADR, deciding build vs buy, or justifying a recommendation to the team or stakeholders.
---

# Technical decisions

## Checklist
- What problem are we solving, and what are the constraints?
- What assumptions are we making?
- At least two options considered (including "do nothing")
- Trade-offs compared on the criteria that matter here
- Reversible or hard to reverse?
- Decision and reasoning written down

## Comparing options
- Simplicity, reliability, security, cost, maintainability, team skills, time to deliver
- Weight criteria by what matters for this problem
- Prototype or spike when uncertainty is high

## Reversible vs irreversible
- Easy to undo (library inside one module): decide quickly
- Hard to undo (database choice, public API, vendor lock-in): slow down, get review

## Build, buy, reuse or do nothing
- Build: core to the business, nothing fits
- Buy/reuse: commodity problem, mature options exist
- Do nothing: cost outweighs benefit right now

## ADRs (Architecture Decision Records)
- Short doc: context, decision, consequences
- One per decision; stored with the code
- Never edited after acceptance; superseded by a new one

## Communicating
- Lead with the recommendation, then reasons and trade-offs
- Be clear about uncertainty and risks

## Further reading
- Documenting architecture decisions (Michael Nygard): https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions
- ADR resources: https://adr.github.io/
