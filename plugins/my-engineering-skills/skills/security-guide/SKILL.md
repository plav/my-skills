---
name: security-guide
description: Security checklist for building and reviewing software. Use when handling authentication, authorisation, user input, secrets, file uploads, payments or personal data, reviewing code for vulnerabilities, or adding dependencies.
---

# Security

## Checklist
- Who can do this? Permissions checked on the server for every request
- All input validated; queries parameterised
- Output encoded to prevent XSS
- Secrets in a secret manager, never in code, logs or tickets
- Least privilege for users, services and keys
- Dependencies up to date and scanned
- Sensitive features: think like an attacker (threat model)

## Authentication vs authorisation
- Authentication: who are you? (login, MFA)
- Authorisation: what are you allowed to do? (roles, ownership checks)
- Common bug: user changes an ID in the URL and sees someone else's data

## OWASP Top 10 (working level)
- Broken access control
- Cryptographic failures (weak or missing encryption)
- Injection (SQL, command)
- Insecure design
- Security misconfiguration
- Vulnerable and outdated components
- Authentication failures
- Software and data integrity failures
- Logging and monitoring failures
- Server-side request forgery (SSRF)
- Note: list is updated periodically; check the current version

## Secrets
- Rotate if exposed; assume anything committed is leaked
- Use pre-commit secret scanning

## Threat modelling (quick)
- What are we building? What can go wrong? What do we do about it? Did it work?

## Lessons from my work
- Never log environment variables, connection strings, credentials or keys, even at startup
- Logged secrets: remove the log, redeploy, rotate the secret, check who could read the logs
- Never log customer data (card data, invoice contents) in plain text
- Snyk findings: check severity, exploit maturity and fixability; upgrade, test, npm audit, retest in Snyk
- PCI-scoped services have extra controls and SLA deadlines on findings

## Further reading
- OWASP Top 10: https://owasp.org/www-project-top-ten/
- OWASP Cheat Sheets: https://cheatsheetseries.owasp.org/
- NCSC (UK): https://www.ncsc.gov.uk/
