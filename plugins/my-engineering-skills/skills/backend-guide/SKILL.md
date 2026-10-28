---
name: backend-guide
description: Checklist for building server-side code and APIs. Use when designing or reviewing an API endpoint, handling validation and errors, structuring services and business logic, or deciding between a monolith and microservices.
---

# Backend

## Checklist
- Consistent naming, status codes and error format
- Validate all input on the server; never trust the client
- Check permissions on every request
- Idempotent writes where retries can happen
- Business logic separate from controllers/handlers
- Timeouts on every outbound call
- Logs with request IDs; no secrets or personal data in logs

## API design
- Resources as nouns (/orders/123), actions via HTTP methods
- GET reads (safe), POST creates, PUT replaces, PATCH updates, DELETE removes
- Status codes: 200 OK, 201 Created, 400 bad input, 401 not logged in, 403 not allowed, 404 not found, 409 conflict, 500 server error
- Paginate lists; filter and sort via query params
- One error shape everywhere (code, message, details)

## Versioning
- Avoid breaking changes: add fields, don't rename or remove
- If you must break: version (/v2) and deprecate with notice

## Idempotency
- Same request twice = same result
- Use idempotency keys for payments and other critical writes

## Structure
- Layers: handler (HTTP) -> service (business logic) -> repository (data)
- Business logic testable without HTTP or a database

## Monolith vs microservices
- Start with a well-structured monolith
- Microservices add network failures, deployment and data complexity
- Split when you have a clear reason: independent scaling, team ownership, release cadence

## Lessons from my work
- Error handlers must never throw: read `err.response?.status`, not a variable from the try block
- Return a clear result ({ success, status }) from wrappers around HTTP calls
- Distinguish "zero" from "unknown": a failed count must not look like 0 and trigger a delete
- Set an explicit HTTP client timeout below the gateway timeout; gateway retries multiply wait time
- Batch jobs: isolate failures per item, record which items failed, carry on with the rest
- Batches must be safe to re-run: check what already succeeded before processing again
- Parameterise SQL even when the value "can't" come from a user

## Further reading
- HTTP status codes (MDN): https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
- The Twelve-Factor App: https://12factor.net/
- REST security cheat sheet (OWASP): https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html
