---
name: bug-investigation-writeup
description: Turns my investigation notes, logs, stack traces and findings into a full bug analysis and acceptance criteria in my team's format. Use whenever I'm investigating a bug, incident or failing job, writing up a root cause, filling in a Jira bug or support request, or asking "what's going on here and how do I write it up?", even if I only paste raw logs and notes.
---

# Bug investigation write-up

## Workflow
1. Read everything provided: notes, logs, stack traces, code snippets, query plans, timelines.
2. List what's confirmed by evidence vs what's an assumption. Never invent evidence, numbers, file paths or timestamps.
3. Build the failure chain from trigger to symptom, one step per line, with file:line where known.
4. Identify the root cause. If not proven, say what would prove it and mark it as a hypothesis.
5. Look for the same defect class elsewhere and for anything a partial fix could make worse.
6. Draft the write-up and acceptance criteria using the templates below.
7. Finish with open questions and gaps I still need to fill (as a short list).

## Rules
- Strip customer names, account numbers, card data, credentials, keys and personal data. Use placeholders like <partner id> or <customer>.
- Use numbers where the evidence gives them (how often, since when, how long).
- Keep code fixes, data fixes and DBA/infra work separate.
- Say explicitly when items must ship together and why.
- Plain language in Impact; technical detail in the failure chain.

## Description template
**Impact** - who/what is affected, how often, since when, what manual work it causes
**Expected behaviour**
**Actual behaviour**
**Failure chain**
- step -> step -> step (file:line)
**Evidence** - logs, timestamps, traces, measurements (sanitised)
**Root cause**
**What needs to change (this ticket)**
1. ... (note dependencies: "must ship with item 2 because ...")
**Also worth fixing while in this code**
**Not in scope** - and who owns it (DBA, infra, product decision, data correction)
**How to verify**
**Other information** - deadlines, risks of waiting, leading indicator to watch after release, links to deeper docs

## Acceptance criteria template
**The Problem** - 2-4 sentences
**The Expected Behaviour** - what good looks like after the fix
**When BAU can consider this Done**
1. Specific, testable outcome (name the test that proves it)
2. ...
Include at least one criterion for the failure path and one for "dangerous side effect does not happen".

## Quality check before finishing
- Could someone who wasn't in the investigation follow the failure chain?
- Is every claim backed by evidence or marked as a hypothesis?
- Is each AC testable by QA?
- Any secrets or customer data left in? Remove them.
