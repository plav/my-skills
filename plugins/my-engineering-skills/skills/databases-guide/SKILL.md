---
name: databases-guide
description: Checklist for data modelling, queries and migrations. Use when designing tables or schemas, writing or optimising queries, adding indexes, writing migrations, choosing SQL vs NoSQL, or debugging slow database performance.
---

# Databases

## Checklist
- Data model designed before code
- Constraints enforce integrity (not null, unique, foreign keys)
- Indexes match the queries actually run
- No N+1 queries
- Migrations backward-compatible and safe on live data
- Multi-step writes inside a transaction

## Modelling
- Normalise first: each fact stored once
- Denormalise only for a measured read-performance need
- Choose types carefully (money as decimal, timestamps with time zone)

## Indexes
- Speed up reads, slow down writes
- Index columns used in WHERE, JOIN, ORDER BY
- Composite index column order matters
- Check the query plan (EXPLAIN) for slow queries

## N+1 queries
- One query for a list, then one per item = N+1
- Fix with joins or eager loading in the ORM

## Migrations
- Small and frequent
- Expand then contract: add new column, backfill, switch code, remove old later
- Large table changes can lock tables; check before running in production
- Some data changes can't be undone: back up first

## Transactions
- All-or-nothing for related writes
- Isolation levels affect what concurrent transactions see

## SQL vs NoSQL
- Default to a relational database
- NoSQL for specific needs: flexible documents, huge scale, key-value caching

## Lessons from my work
- EXPLAIN (ANALYZE, BUFFERS) on a read replica shows real cost; check rows scanned vs returned
- Cold vs warm cache can make the same query 10x+ slower; intermittent slowness often means this
- Stale statistics and dead tuples slow queries: ANALYZE and VACUUM, check autovacuum thresholds
- Queries with no lower date bound scan all history; growing tables make it worse every month
- Separate code fixes from DBA work (indexes, archiving, memory) and data corrections

## Further reading
- Use The Index, Luke: https://use-the-index-luke.com/
- PostgreSQL docs: https://www.postgresql.org/docs/
- Book: Designing Data-Intensive Applications, Martin Kleppmann
