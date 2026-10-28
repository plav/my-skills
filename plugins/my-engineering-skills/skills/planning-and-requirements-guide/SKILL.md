---
name: planning-and-requirements-guide
description: Checklist for planning work and defining requirements. Use when starting a new feature, ticket or project, writing or reviewing user stories and acceptance criteria, clarifying scope, or checking whether requirements are clear enough to start building.
---

# Planning and requirements

## Checklist
- What problem are we solving, for whom, and how will we know it worked?
- Functional (what it does) vs non-functional (speed, scale, security) requirements
- Non-functional requirements are measurable: say how they'll be checked
- User stories: "As a <user>, I want <goal>, so that <reason>"
- Stories follow INVEST: Independent, Negotiable, Valuable, Estimable, Small, Testable
- Acceptance criteria: specific, testable, written from the user's view, agreed before starting
- Definition of Done: the team's quality bar for every item (tested, reviewed, documented, deployed)
- Scope, priorities, feasibility; write down assumptions and open questions
- Too big? Split it into smaller stories before estimating

## What is agile
- Deliver in small increments, get feedback, adapt
- Agile Manifesto values: people over process, working software over docs, customer collaboration over contracts, responding to change over following a plan
- Scrum: fixed-length sprints with planning, daily standup, review, retro
- Kanban: continuous flow, limit work in progress, no fixed sprints

## Refinement
- Regular session to get backlog items ready before sprint planning
- Clarify the story, add acceptance criteria, split if too big, estimate
- Raise questions, dependencies and risks early
- "Ready" = team understands it well enough to start

## What is a user story
- Small piece of value described from the user's point of view
- Format: As a <user>, I want <goal>, so that <reason>
- 3 Cs: Card (short description), Conversation (details agreed by talking), Confirmation (acceptance criteria)
- Not a technical task: "Refactor payment module" is a task, not a story

## Breakdown: Epic - Story - Task - Subtask
- Epic: large body of work spanning multiple sprints (e.g. "User accounts")
- Story: user-facing value deliverable in one sprint (e.g. "Reset password")
- Task: technical work, often same level as a story in Jira (e.g. "Set up email service")
- Subtask: smallest step within a story or task (e.g. "Add reset endpoint")
- Split stories vertically (thin slice through UI, API, DB), not by layer

## Acceptance criteria
- Conditions a specific story must meet to be accepted
- Testable, clear pass/fail, written before work starts
- Cover happy path, edge cases and errors
- Given/When/Then format: Given <context>, When <action>, Then <outcome>
- Describe what, not how

## Definition of done
- Team-wide quality bar that applies to every item
- Typical: code reviewed, tests pass, acceptance criteria met, docs updated, deployed to agreed environment
- Acceptance criteria = per story; Definition of Done = for everything
- Not done = not released

## Feedback
- Sprint review/demo: show working software to stakeholders
- Retro: what went well, what didn't, one or two actions to improve
- Get feedback early: share drafts, prototypes, partial work
- Check outcomes after release (metrics, user feedback)

## Time
- Story points measure relative effort and uncertainty, not hours
- Estimate as a team (e.g. planning poker); big differences = discuss
- Velocity: points completed per sprint, used for planning, not performance
- Unknowns? Timebox a spike (research task) before estimating
- Flag early if an estimate is wrong

## INVEST
- Independent: can be built in any order
- Negotiable: details agreed through conversation, not a fixed contract
- Valuable: delivers value to a user or the business
- Estimable: understood well enough to estimate
- Small: fits in a sprint
- Testable: clear criteria to check it works
- A guide, not a gate

## Other principles
- MVP: smallest thing that tests whether the idea works
- MoSCoW prioritisation: Must, Should, Could, Won't (this time)
- YAGNI: don't build for imagined future needs
- Outcomes over outputs: problems solved matter more than features shipped
- Raise risks, assumptions and dependencies as early as possible

## Functional requirements
- What the system does: features, behaviours, rules
- Example: users can reset their password via email
- Captured as user stories and acceptance criteria

## Non-functional requirements
- How well the system does it: quality attributes and constraints
- Types: performance, scalability, availability, security, usability, accessibility, compliance (e.g. GDPR)
- Must be measurable: "page loads in under 2s for 95% of requests", not "fast"
- Often apply across many stories; consider adding them to the Definition of Done

## Further reading
- User stories (Atlassian): https://www.atlassian.com/agile/project-management/user-stories
- Acceptance criteria (Atlassian): https://www.atlassian.com/work-management/project-management/acceptance-criteria
- INVEST explained: https://t2informatik.de/en/smartpedia/invest-principle/
- INVEST video by Bill Wake: https://www.industriallogic.com/blog/the-invest-model-for-user-stories/
- Non-functional requirements (Microsoft Learn): https://learn.microsoft.com/en-us/training/modules/work-with-requirements/4-non-functional-requirements
- Definition of Done: https://www.ministryoftesting.com/software-testing-glossary/defintion-of-done
