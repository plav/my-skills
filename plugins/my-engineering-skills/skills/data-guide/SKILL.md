---
name: data-guide
description: Checklist for working with data pipelines, data quality and personal data. Use when moving or transforming data between systems, building reports or pipelines, checking data quality, or handling personal data and GDPR concerns.
---

# Data

## Checklist
- Where does the data come from, and who owns it?
- How fresh does it need to be (real-time, hourly, daily)?
- How is quality checked?
- Does it contain personal data? Can we avoid storing it?
- How long is it kept, and how is it deleted?

## Pipelines
- ETL: extract, transform, load. ELT: load first, transform in the warehouse
- Batch (scheduled) vs streaming (continuous)
- Pipelines should be re-runnable without creating duplicates
- Monitor runs and alert on failure or late data

## Data quality
- Check for nulls, duplicates, out-of-range values, schema changes
- Validate at the boundary when data comes in
- Track where data came from (lineage)

## Personal data and privacy
- Collect only what's needed (data minimisation)
- Know the lawful basis and retention period
- Restrict access; mask or anonymise for testing and analytics
- UK/EU: UK GDPR and EU GDPR apply; check company policy

## Further reading
- ICO guide to UK GDPR: https://ico.org.uk/for-organisations/
- Book: Designing Data-Intensive Applications, Martin Kleppmann
