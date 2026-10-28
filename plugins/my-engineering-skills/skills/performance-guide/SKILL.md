---
name: performance-guide
description: Checklist for finding and fixing performance problems. Use when something is slow, before optimising code, when adding caching, pagination or lazy loading, or when reviewing front-end load times or back-end latency.
---

# Performance

## Checklist
- Is there a real problem? Measure first
- Find the bottleneck before changing anything
- Fix the biggest cost first; re-measure after
- Set a target (e.g. p95 response under 300ms)

## Measuring
- Profilers for CPU and memory
- Percentiles (p50, p95, p99), not averages
- Browser devtools: network and performance tabs
- Load testing for capacity

## Common back-end fixes
- N+1 queries and missing indexes
- Too many network calls: batch or run in parallel
- Pagination for large lists
- Move slow work to background jobs

## Caching
- Cache what's expensive and read often
- Decide expiry (TTL) and how to invalidate on change
- Stale data: is it acceptable here, and for how long?
- Cache stampede: many requests rebuild at once; use locking or early refresh

## Front-end
- Smaller bundles, compressed images, lazy loading
- Avoid unnecessary re-renders
- Core Web Vitals: loading (LCP), responsiveness (INP), visual stability (CLS)

## Further reading
- Web Vitals: https://web.dev/articles/vitals
- USE method (Brendan Gregg): https://www.brendangregg.com/usemethod.html
