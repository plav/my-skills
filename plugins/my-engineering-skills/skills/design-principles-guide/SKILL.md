---
name: design-principles-guide
description: Checklist for designing modules, components and system structure. Use when planning how to structure new code, splitting a feature into parts, reviewing a design, or when code feels tangled or hard to change.
---

# Design principles

## Checklist
- Can each part be explained in one sentence?
- High cohesion: related things together; each module does one job
- Low coupling: changing one part rarely breaks another
- Hide details behind simple interfaces
- Simplest design that meets the requirements
- Prototype or mock up UI before building it

## Modularity
- Split by business capability (auth, cart, billing), not just technical layer
- Clear boundaries: modules talk through defined interfaces, not each other's internals
- Dependencies point one way; avoid circular dependencies

## Cohesion and coupling
- Cohesion signs: changes for one reason land in one place
- Coupling signs: one small change touches many files; shared mutable state; deep imports
- Reduce coupling with interfaces, events, or passing data in rather than reaching out

## Complexity
- Complexity = what makes code hard to understand and change
- Deep modules: simple interface, lots of useful work behind it
- Don't add layers or abstractions until they pay for themselves

## Prototypes and mockups
- Wireframes or quick prototypes to get feedback before building
- Throw prototypes away; don't ship them by accident

## Further reading
- Book: A Philosophy of Software Design, John Ousterhout
- Coupling (Wikipedia): https://en.wikipedia.org/wiki/Coupling_(computer_programming)
- Martin Fowler's bliki: https://martinfowler.com/bliki/
