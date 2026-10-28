---
name: devops-cicd-guide
description: Checklist for build pipelines, deployment and release. Use when setting up or debugging CI/CD, writing Dockerfiles, managing environment config, planning a deploy or rollback, or using feature flags.
---

# DevOps and CI/CD

## Checklist
- Do I know how code gets from merge to production?
- Can I roll back, and how fast?
- Pipeline runs build, lint, tests and security scans on every change
- Config comes from the environment, not hard-coded
- Same build artefact promoted through environments
- Risky change? Use a feature flag

## CI (continuous integration)
- Merge small changes often
- Every change builds and tests automatically
- Broken main branch gets fixed first

## CD (continuous delivery/deployment)
- Delivery: always releasable, deploy on a button
- Deployment: every passing change goes live automatically

## Containers
- Package app and dependencies together (Docker)
- Small base images; don't run as root
- Pin versions for repeatable builds

## Config and environments
- Dev, test/staging, production
- Secrets injected at runtime from a secret manager

## Release strategies
- Feature flags: deploy dark, release when ready; clean up old flags
- Canary: release to a small % first
- Blue-green: switch traffic between two environments

## Debugging a failed pipeline
- Read the first error, not the last
- Reproduce locally; check what changed

## Lessons from my work
- Releases here: make commands or a GitHub Actions workflow, plus a separate env-config repo
- Check config values exist for every environment; a missing value can make QA call production services
- A console hotfix (e.g. editing a Lambda directly) must be merged back to git immediately
- Before deploying a batch service, confirm no run is in progress

## Further reading
- Feature toggles (Martin Fowler): https://martinfowler.com/articles/feature-toggles.html
- The Twelve-Factor App: https://12factor.net/
- Docker get started: https://docs.docker.com/get-started/
