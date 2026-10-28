---
name: qa-test-steps-writer
description: Writes QA test steps from acceptance criteria, a ticket or a PR description, in my team's format. Use whenever a ticket is moving to Ready for QA, I need to fill in BAU Test Steps, I'm asked "how should this be tested?", or I paste acceptance criteria or a change summary and need a test plan.
---

# QA test steps writer

## Workflow
1. Read the acceptance criteria, change summary and any known issues.
2. Map each AC to at least one test. Flag any AC that can't be tested as written.
3. Work out prerequisites: access/permissions, tools, environment, test data.
4. Write tests for the happy path, failure paths, edge cases and regressions.
5. For failure paths, explain how to force the failure in QA and how to undo it.
6. Add cleanup steps and anything the tester must NOT do.
7. List assumptions and questions for me to confirm (e.g. exact endpoint names, expected messages).

## Rules
- Write so a tester who didn't build it can follow it alone.
- Expected results must be observable: response codes/bodies, UI state, log lines, DB rows.
- Use placeholders for IDs and data; never include real customer data or credentials.
- Don't invent endpoint names, log messages or commands; mark them <confirm> if unsure.

## Template
**Prerequisites**
- Access/permissions:
- Tools: (e.g. Postman collection, k9s, Datadog search, browser dev tools)
- Environment and test data:

**Known existing issues** (not introduced by this change)

**Test 1 - <name> (AC1, AC2)**
1. Step
2. Step
Expected:
- ...

**Test N - Failure path: <what fails> (ACx)**
1. How to force it (and note: revert afterwards)
2. Steps
Expected:
- Failure is contained, clearly logged, nothing else affected

**Regression**
- Neighbouring features that should behave exactly as before

**Unit tests**
- Command: <e.g. npm test>
- Expected: <n> suites / <n> tests pass

**Cleanup**
- Remove test data; anything not to click or trigger
