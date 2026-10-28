---
name: documentation-guide
description: Checklist for writing technical documentation. Use when writing or updating a README, how-to guide, runbook, API docs or ADR, documenting how something works, or onboarding someone to a project.
---

# Documentation

## Checklist
- Who is the reader and what do they need to do?
- README covers: what it is, how to run it, how to test it, how to deploy
- Decisions recorded with the why (ADRs)
- Docs updated in the same PR as the change
- Examples included and working
- Out-of-date docs removed

## Types of docs (Diátaxis)
- Tutorial: learning by doing, for beginners
- How-to guide: steps to achieve a specific goal
- Reference: facts (API, config options)
- Explanation: background and why

## README
- One-line description
- Prerequisites and setup
- Run, test, deploy commands
- Where to get help

## Runbooks
- Symptom, likely causes, steps to check, steps to fix, who to escalate to

## Writing tips
- Short sentences, plain language
- Lead with the most important information
- Headings and code blocks for scanning
- Docs close to the code are more likely to stay current

## Lessons from my work
- SOP structure: metadata (author, approver, status, contacts, time, frequency), description, risks, requirements, steps, exit criteria, review history
- Deep analysis lives in the repo (docs/plans), the ticket links to it
- Write release "Change / Reason / Impact" for non-engineers

## Further reading
- Diátaxis: https://diataxis.fr/
- Write the Docs guide: https://www.writethedocs.org/guide/
- ADRs: https://adr.github.io/
