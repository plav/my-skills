---
name: concurrency-and-async-guide
description: Checklist for concurrent and asynchronous code. Use when writing async code, background jobs or scheduled tasks, handling simultaneous updates to the same data, or debugging intermittent bugs that might be race conditions or deadlocks.
---

# Concurrency and async

## Checklist
- Can two requests or jobs touch the same data at once?
- Is shared mutable state protected?
- Are background jobs safe to retry and run twice?
- Does any blocking call stall an event loop?
- Is this work better done synchronously or in the background?

## Common problems
- Race condition: result depends on timing (two users buy the last item)
- Deadlock: two operations wait on each other forever
- Lost update: two writes, one silently overwrites the other

## Tools
- Database transactions and constraints (unique keys catch duplicates)
- Pessimistic locking: lock the row first (SELECT ... FOR UPDATE)
- Optimistic concurrency: version column; reject the write if it changed
- Atomic operations: increment in the database, not read-modify-write in code
- Prefer immutable data and message passing over shared state

## Background jobs
- Use for slow or non-urgent work (emails, reports, imports)
- Idempotent: running twice causes no harm
- Retries with backoff; dead-letter after repeated failure
- Monitor queue length, failures and job duration

## Sync vs async
- Sync: user needs the result now, and it's fast
- Async: slow, can fail and retry, or user doesn't need to wait

## Lessons from my work
- Execution locks released in `finally` are only safe if all work is actually finished
- Un-awaited timers/callbacks (e.g. setInterval) keep working after the lock is released and their errors escape try/catch
- Protect against double-submit (repeated clicks) on long-running triggers
- Overlapping runs can create duplicates; check before investigating "missing" data

## Further reading
- PostgreSQL transaction isolation: https://www.postgresql.org/docs/current/transaction-iso.html
- Book: Designing Data-Intensive Applications, Martin Kleppmann (chapter on transactions)
