---
name: clean-code-guide
description: Checklist for writing readable, maintainable code. Use when writing or refactoring code, naming things, choosing whether to abstract or use a design pattern, or reviewing code quality, including my own before raising a PR.
---

# Clean code

## Checklist
- Names say what something is or does; no unexplained abbreviations
- Functions small and doing one thing
- Consistent formatting (automate with a formatter and linter)
- Comments explain why, not what
- No dead code or commented-out code
- Refactor in separate commits from behaviour changes

## Principles (defaults, not rules)
- SOLID: Single responsibility, Open/closed, Liskov substitution, Interface segregation, Dependency inversion
- DRY: don't repeat knowledge; a little duplication beats a bad abstraction
- KISS: simplest thing that works
- YAGNI: don't build for imagined needs
- Rule of three: abstract on the third repetition, not the first

## Design patterns
- Common: Factory, Strategy, Observer, Adapter, Decorator
- Use when the problem matches; don't force a pattern in
- Singleton often hides global state; prefer passing dependencies in

## Refactoring
- Have tests before refactoring
- Small steps, run tests after each
- Common moves: extract function, rename, inline, move, replace conditional with polymorphism
- Leave code a bit better than you found it

## Code smells
- Long functions, long parameter lists, deep nesting
- Duplicated logic, magic numbers, boolean flag parameters
- Classes that know too much about others

## Further reading
- Refactoring catalogue: https://refactoring.guru/refactoring
- Design patterns: https://refactoring.guru/design-patterns
- Book: Refactoring, Martin Fowler
- Book: Clean Code, Robert C. Martin (read critically; some advice is dated)
