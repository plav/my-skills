---
name: code-review-guide
description: Checklist for reviewing code and raising pull requests. Use when reviewing someone's PR, self-reviewing my own changes before raising a PR, writing a PR description, or responding to review feedback.
---

# Code review

## Reviewing checklist
- Does it do what the ticket asks? Acceptance criteria met?
- Correct: edge cases, errors, nulls, concurrency
- Secure: input validation, permissions, no secrets
- Tested: meaningful tests, including failure cases
- Readable: names, structure, comments where needed
- Fits the design and conventions of the codebase
- No unnecessary complexity

## Order of attention
1. Design and approach
2. Correctness and security
3. Tests
4. Readability
5. Style (let linters handle it)

## Giving feedback
- Specific, kind, about the code not the person
- Explain why, suggest an alternative
- Label severity: blocking, suggestion, nit, question
- Praise good work too
- Big disagreements: talk, don't argue in comments

## Raising a PR
- Small and focused; one purpose
- Description: what, why, how to test, screenshots for UI
- Self-review the diff first
- Link the ticket

## Receiving feedback
- Assume good intent; ask if unclear
- Reply to every comment (fixed, or why not)

## Lessons from my work
- Review error paths as carefully as the happy path: can the catch block itself throw?
- Look for "same defect class" elsewhere in the codebase and list it
- Check logs added in the PR for secrets or customer data
- Check what happens if half the fix ships without the other half

## Further reading
- Google engineering practices, code review: https://google.github.io/eng-practices/review/
- Conventional Comments: https://conventionalcomments.org/
