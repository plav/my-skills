---
name: distributed-systems-guide
description: Checklist for systems that talk over a network. Use when calling other services or APIs, adding retries, using message queues, handling partial failures, designing for eventual consistency, or debugging duplicate or out-of-order events.
---

# Distributed systems and resilience

## Checklist
- Every network call has a timeout
- Retries use backoff and jitter, and only for safe/idempotent operations
- Duplicates handled (idempotency keys, dedupe)
- Out-of-order messages handled
- Single points of failure identified
- Behaviour defined when a dependency is down

## Assume the network fails
- Calls can fail, time out, be slow, succeed twice, or succeed but lose the reply
- A timeout doesn't mean it didn't happen

## Retries
- Exponential backoff with jitter to avoid everyone retrying at once
- Cap the number of retries
- Retrying at every layer multiplies load (retry storm)

## Protecting the system
- Circuit breaker: stop calling a failing dependency for a while
- Rate limiting: cap requests per client
- Backpressure: slow producers when consumers can't keep up
- Bulkheads: isolate resources so one failure doesn't take all down

## Queues
- At-least-once delivery is common: expect duplicates
- Dead-letter queue for messages that keep failing
- Monitor queue depth and age

## Consistency
- Eventual consistency: data agrees after a delay; design the UI for it
- Outbox pattern: save data and event together so neither is lost

## Lessons from my work
- Infrastructure retries (e.g. 3 x 120s at the gateway) can turn one slow call into a 6-minute stall
- App timeout should fail fast unless a longer one is deliberate and documented
- One slow downstream dependency should affect only the work that needs it
- Track the leading indicator (does attempt 1 succeed?), not just whether the run survived

## Further reading
- Timeouts, retries and backoff with jitter (AWS): https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/
- Amazon Builders' Library: https://aws.amazon.com/builders-library/
- Book: Designing Data-Intensive Applications, Martin Kleppmann
