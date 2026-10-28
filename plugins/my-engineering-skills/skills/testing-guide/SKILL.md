---
name: testing-guide
description: Checklist for testing strategy and writing good tests. Use when writing or reviewing tests, deciding what and how to test, fixing a bug, dealing with flaky tests, or checking whether a change is tested enough to ship.
---

# Testing

## Checklist
- What's the risk if this breaks? Test proportionally
- Tests check behaviour, not implementation details
- Happy path, edge cases and error cases covered
- Every bug fix has a regression test
- Tests are fast, isolated and deterministic
- Test names read like a spec

## Types
- Unit: one function or class, fast, many of these
- Integration: parts working together (API + database)
- End-to-end: whole system through the UI, few of these (slow, brittle)
- Contract: services agree on API shape
- Acceptance: meets the user's acceptance criteria

## Choosing the mix
- Unit-heavy (test pyramid) is a common default
- More integration tests where the risk is in the connections
- Pick by confidence needed, not by dogma

## Good tests
- Arrange, Act, Assert structure
- One reason to fail per test
- Avoid excessive mocking; mock at boundaries (network, time, randomness)
- Test data built clearly in the test

## Flaky tests
- Fix or quarantine immediately; they destroy trust in the suite
- Usual causes: timing, shared state, test order, real network calls

## Coverage
- A guide to find gaps, not a target to hit
- 100% coverage can still miss the important cases

## TDD
- Red (failing test), green (make it pass), refactor
- Useful for logic-heavy code and bug fixes

## Lessons from my work
- Write test steps a QA tester can follow without me: prerequisites, expected results, cleanup
- Map each test to an acceptance criterion
- Unit test failure paths explicitly (503, timeout, no response object)
- Assert dangerous side effects do NOT happen (e.g. nothing deleted on failure)
- Forcing a failure in QA with a temporary config change is fine; always note to revert it

## Further reading
- The Practical Test Pyramid: https://martinfowler.com/articles/practical-test-pyramid.html
- Testing Library guiding principles: https://testing-library.com/docs/guiding-principles
