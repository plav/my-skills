---
name: cs-fundamentals-guide
description: Quick reference for computer science fundamentals. Use when choosing a data structure, judging algorithm efficiency, reasoning about memory, threads or the event loop, debugging networking issues, or preparing for technical interviews.
---

# Computer science fundamentals

## Checklist
- Right data structure for the access pattern?
- What's the Big O? Any hidden loop inside a loop?
- Where does this run: which process, thread, event loop?
- What crosses the network, and what if it's slow or fails?

## Data structures
- Array/list: ordered, fast index lookup, slow search O(n)
- Hash map/set: fast lookup by key O(1) average, no order
- Tree: sorted data, range queries, hierarchies; balanced = O(log n)
- Graph: relationships (networks, dependencies)
- Queue (FIFO) / stack (LIFO): processing order
- Heap: always get the smallest/largest quickly (priority queue)

## Big O
- O(1) constant, O(log n) halving, O(n) one pass, O(n log n) good sort, O(n²) nested loops
- Watch for: searching a list inside a loop (use a set/map instead)
- Space matters too: copying large collections, caching everything

## Algorithms
- Searching: linear vs binary search (needs sorted data)
- Sorting: use the language's built-in sort
- Traversal: breadth-first (shortest path, levels) vs depth-first (explore fully)
- Recursion: needs a base case; deep recursion can overflow the stack

## Runtime
- Process: own memory. Thread: shares memory with others in the process
- Event loop (JS, Python asyncio): single thread; blocking code stalls everything
- Garbage collection: frees unused memory; leaks come from references held too long

## Networking
- DNS: name to IP. TCP: reliable connection. TLS: encryption. HTTP: request/response on top
- Latency adds up per call; batch or parallelise
- Always set timeouts

## Further reading
- Big O cheat sheet: https://www.bigocheatsheet.com/
- High Performance Browser Networking (free online): https://hpbn.co/
- Teach Yourself CS (study plan): https://teachyourselfcs.com/
