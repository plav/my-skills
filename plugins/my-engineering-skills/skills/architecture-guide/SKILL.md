---
name: architecture-guide
description: Checklist for system architecture and design trade-offs. Use when designing a new system or major feature, evaluating scalability, choosing between sync and async or caching and queues, preparing for system design interviews, or asking "what happens when X goes down?".
---

# Architecture

## Checklist
- What are the key requirements and constraints (scale, latency, cost, team)?
- What are the main components and how do they talk?
- Where is data stored, and who owns it?
- What happens when each component fails?
- How does it scale, and where's the bottleneck?
- Simplest architecture that meets the needs?

## Key trade-offs
- Sync (simple, immediate) vs async (resilient, decoupled, harder to trace)
- Caching (fast) vs freshness (correct)
- Consistency vs availability when the network splits
- Monolith (simple) vs services (independent but complex)
- Build vs buy

## Scaling
- Vertical: bigger machine. Horizontal: more machines
- Stateless services scale horizontally easily
- Databases are usually the hardest part to scale (read replicas, partitioning)
- Queues smooth out spikes

## Common building blocks
- Load balancer, cache, queue, database, object storage, CDN

## Failure modes
- Single points of failure
- Cascading failures from slow dependencies
- Plan degradation: what still works if X is down?

## System design interviews
- Clarify requirements, estimate scale, sketch high level, deep-dive one area, discuss trade-offs

## Further reading
- Martin Fowler on architecture: https://martinfowler.com/architecture/
- AWS Well-Architected: https://aws.amazon.com/architecture/well-architected/
- Book: Fundamentals of Software Architecture, Richards and Ford
