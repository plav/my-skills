---
name: observability-and-debugging-guide
description: Method and checklist for debugging and observability. Use when investigating a bug, error or incident, something works locally but not in production, adding logging, metrics or tracing, or when stuck on a problem and need a structured approach.
---

# Observability and debugging

## Checklist
- Can I reproduce it? What are the exact steps and environment?
- What changed recently (code, config, data, dependencies)?
- What do logs, metrics and traces show?
- One hypothesis at a time; test it; record the result
- Fix the cause, add a regression test, write up what I learned

## Debug loop
1. Reproduce reliably
2. Narrow down (binary search: git bisect, comment out, smaller input)
3. Hypothesise a cause
4. Verify with evidence, not assumption
5. Fix and confirm the fix

## Useful techniques
- Read the full error and stack trace; start from the first error
- Debugger and breakpoints over print statements when possible
- Explain the problem out loud (rubber duck)
- Check assumptions: is it running the code I think it is?
- Take a break if stuck; ask someone after a timebox

## Logs
- Structured (JSON) with request/correlation IDs
- Levels: error, warn, info, debug
- No secrets or personal data

## Metrics and tracing
- Metrics: counts, rates, durations; alert on user impact
- Tracing: follow one request across services (OpenTelemetry)

## Write-ups
- Symptom, cause, fix, how to spot it next time

## Lessons from my work
- console.warn/console.log can land on stderr and be ingested as errors; use the logger with correct levels
- Reserve error level for things that actually stop work, so real failures stand out
- Log every item dropped from a batch with its reason; silent drops can't be verified
- Build the failure chain from evidence: access logs, timestamps, stack traces, query plans
- Compare failed and successful runs side by side
- Tools here: Datadog log search, k9s / kubectl for pod logs, CloudWatch for Lambdas

## Further reading
- Effective troubleshooting (Google SRE book): https://sre.google/sre-book/effective-troubleshooting/
- OpenTelemetry docs: https://opentelemetry.io/docs/
- Book: Debugging, David Agans (9 rules)
