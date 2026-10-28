# my-skills

A Claude Code plugin marketplace: 240 skills in 20 plugins. Each plugin is a folder under `plugins/`; each skill is a folder with a `SKILL.md`. Delete or add folders freely.

## Install

```
claude plugin marketplace add plav/my-skills
claude plugin install my-engineering-skills@my-skills
```

Install only the plugins you want: `claude plugin install <plugin>@my-skills`. Restart Claude Code after installing. For this private repo, set a `GITHUB_TOKEN` (fine-grained, read access to this repo only) before starting Claude Code, or updates can fail silently.

## Update

1. Edit skills.
2. Bump `version` in that plugin's `.claude-plugin/plugin.json`. Same version means no update.
3. Push, then on each machine:

```
claude plugin marketplace update my-skills
claude plugin update <plugin>@my-skills
```

## Add or remove

- **Add a skill:** drop a folder with `SKILL.md` into `plugins/<plugin>/skills/`, bump the version.
- **Remove a skill:** delete its folder, bump the version.
- **Add a plugin:** create `plugins/<name>/.claude-plugin/plugin.json` and add an entry to `.claude-plugin/marketplace.json`.
- **Remove a plugin:** delete its folder and its entry in `marketplace.json`.

## Duplicates removed (v1.1.0)

No two skills share a name now. Removed, so the stronger copy fires:

- **`matt-pocock-skills`:** 24 skills that `supermatt-skills` also has. The supermatt copies were longer and newer in every case. Matt's unique skills stay.
- **`code-review-plugin`:** whole plugin removed. Its one skill had a one-line description that fired on anything PR-shaped.
- **`engineering-workflows/code-review`:** removed; `supermatt-skills/code-review` covers standards, spec and adversarial review.
- **`engineering-team-roles/commit`:** removed; it had no frontmatter. `supermatt-skills/commit` stays (manual only).
- **`supermatt-skills/handoff`:** removed; `workflow-studio/handoff` stays (pairs with `done`).

All removals are in git history; restore with `git checkout <commit>^ -- <path>`.

## Same job, different names

These no longer clash by name but still overlap in purpose. Install one per row if skills fight to fire:

| Job | Skills |
|---|---|
| Code review | supermatt `code-review`, superpowers `requesting-code-review`, my `code-review-guide`, workflow-studio `code-quality` |
| Debugging | superpowers `systematic-debugging`, supermatt `diagnosing-bugs`, engineering-workflows `debug`, backend-discipline `debugging-discipline`, workflow-studio `debugging-and-error-recovery`, my `observability-and-debugging-guide` |
| TDD | superpowers `test-driven-development`, supermatt `tdd`, workflow-studio `tdd-skill` |
| Security | my `security-guide`, backend-discipline `security-discipline`, workflow-studio `security-and-hardening`, engineering-team-roles `security-engineer`, security-scanner `claude-security`, extra `differential-review`/`sharp-edges` |

## Before you share

- **Licenses.** Only `my-engineering-skills` is yours. Many packs had no license file, and their source names are guessed from contents. Keep this repo private.
- **Work content.** `my-engineering-skills` describes how your team works. `ticket-kickoff` contains a real Jira project key as an example.
- **Tool-dependent skills.** `codeql`, `semgrep`, `webapp-testing`, `mcp-server-builder`, the `datadog` plugin and others need local tools, MCP servers or network access.
- **Manual-only skills** are marked _(manual)_ below: they never fire on their own; call them with `/name`.

## Plugins at a glance

| Plugin | Skills | Source | License |
|---|---|---|---|
| [`my-engineering-skills`](#my-engineering-skills) | 39 | Your own skills | Yours |
| [`extra-skills`](#extra-skills) | 10 | Trail of Bits, wshobson/agents, Karpathy, Anthropic | License file kept in each skill folder |
| [`superpowers`](#superpowers) | 15 | obra/superpowers (guessed from contents) | Unknown, not bundled. |
| [`matt-pocock-skills`](#matt-pocock-skills) | 14 | Matt Pocock skills (guessed) | Unknown, not bundled. |
| [`supermatt-skills`](#supermatt-skills) | 38 | fork/variant of Matt Pocock skills (guessed) | Unknown, not bundled. |
| [`engineering-team-roles`](#engineering-team-roles) | 14 | 10x-team role pack (unknown author) | Unknown, not bundled. |
| [`backend-discipline`](#backend-discipline) | 18 | senior backend discipline pack (unknown author) | Unknown, not bundled. |
| [`sanity`](#sanity) | 11 | Sanity (guessed from contents) | Unknown, not bundled. |
| [`engineering-workflows`](#engineering-workflows) | 9 | engineering workflow pack (unknown author) | Unknown, not bundled. |
| [`data-analysis`](#data-analysis) | 10 | data analysis pack (unknown author) | Unknown, not bundled. |
| [`design`](#design) | 7 | design pack (unknown author) | Unknown, not bundled. |
| [`workflow-studio`](#workflow-studio) | 36 | full-stack workflow pack, Vue/Tabler flavoured (unknown author) | Unknown, not bundled. |
| [`productivity`](#productivity) | 4 | productivity pack (unknown author) | Unknown, not bundled. |
| [`security-scanner`](#security-scanner) | 1 | Claude Security menu plugin (unknown author) | Unknown, not bundled. |
| [`cv-builder`](#cv-builder) | 4 | CV Builder plugin (unknown author) | Unknown, not bundled. |
| [`ai-mentor`](#ai-mentor) | 1 | AI workflow mentor plugin (unknown author) | Unknown, not bundled. |
| [`caveman`](#caveman) | 1 | caveman (guessed JuliusBrussee/caveman) | Unknown, not bundled. |
| [`humanizer`](#humanizer) | 1 | humanizer pack | License file bundled. |
| [`modern-web-guidance`](#modern-web-guidance) | 2 | modern-web-guidance plugin | Unknown, not bundled. |
| [`datadog`](#datadog) | 5 | Datadog plugin | Unknown, not bundled. Needs the Datadog MCP server to work. |

## Skills by plugin

Descriptions are taken from each skill's own `SKILL.md`.

### my-engineering-skills

Source: Your own skills. License: Yours

| Skill | What it does |
|---|---|
| `ai-guide` | Checklist for using AI in engineering work and building AI features. Use when prompting AI tools, setting up Claude Code with CLAUDE.md, skills, hooks or MCP, reviewing AI-generated code, building features that call an LLM, or writing evals. |
| `architecture-guide` | Checklist for system architecture and design trade-offs. Use when designing a new system or major feature, evaluating scalability, choosing between sync and async or caching and queues, preparing for system design interviews, or asking "what happens when X goes down?". |
| `backend-guide` | Checklist for building server-side code and APIs. Use when designing or reviewing an API endpoint, handling validation and errors, structuring services and business logic, or deciding between a monolith and microservices. |
| `bau-workflow-guide` | How my current team works day to day in BAU (support engineering). Use whenever I'm picking up, writing or updating a Jira ticket at work, writing a bug analysis, test steps, a release ticket or an SOP, preparing for CAB, or handing work to QA or Production Services. Based on patterns in my own tickets; never put customer names, credentials or personal data in anything written from it. |
| `bug-investigation-writeup` | Turns my investigation notes, logs, stack traces and findings into a full bug analysis and acceptance criteria in my team's format. Use whenever I'm investigating a bug, incident or failing job, writing up a root cause, filling in a Jira bug or support request, or asking "what's going on here and how do I write it up?", even if I only paste raw logs and notes. |
| `calls-and-preparation-guide` | Checklist for preparing for and running meetings and calls. Use before a meeting, stakeholder call, technical discussion, 1:1, demo or interview, to plan goals and questions, and afterwards to write up notes and actions. |
| `career-growth-guide` | Checklist for career development as a software engineer. Use when preparing for reviews, retros or 1:1s, updating a CV, planning learning, thinking about promotion or the next level, or preparing for interviews. |
| `clean-code-guide` | Checklist for writing readable, maintainable code. Use when writing or refactoring code, naming things, choosing whether to abstract or use a design pattern, or reviewing code quality, including my own before raising a PR. |
| `cloud-guide` | Checklist for working with cloud platforms. Use when choosing or configuring cloud services, setting up IAM permissions, writing infrastructure as code, estimating or reducing cloud costs, or reviewing cloud security. |
| `code-review-guide` | Checklist for reviewing code and raising pull requests. Use when reviewing someone's PR, self-reviewing my own changes before raising a PR, writing a PR description, or responding to review feedback. |
| `concurrency-and-async-guide` | Checklist for concurrent and asynchronous code. Use when writing async code, background jobs or scheduled tasks, handling simultaneous updates to the same data, or debugging intermittent bugs that might be race conditions or deadlocks. |
| `cs-fundamentals-guide` | Quick reference for computer science fundamentals. Use when choosing a data structure, judging algorithm efficiency, reasoning about memory, threads or the event loop, debugging networking issues, or preparing for technical interviews. |
| `data-guide` | Checklist for working with data pipelines, data quality and personal data. Use when moving or transforming data between systems, building reports or pipelines, checking data quality, or handling personal data and GDPR concerns. |
| `databases-guide` | Checklist for data modelling, queries and migrations. Use when designing tables or schemas, writing or optimising queries, adding indexes, writing migrations, choosing SQL vs NoSQL, or debugging slow database performance. |
| `design-principles-guide` | Checklist for designing modules, components and system structure. Use when planning how to structure new code, splitting a feature into parts, reviewing a design, or when code feels tangled or hard to change. |
| `devops-cicd-guide` | Checklist for build pipelines, deployment and release. Use when setting up or debugging CI/CD, writing Dockerfiles, managing environment config, planning a deploy or rollback, or using feature flags. |
| `distributed-systems-guide` | Checklist for systems that talk over a network. Use when calling other services or APIs, adding retries, using message queues, handling partial failures, designing for eventual consistency, or debugging duplicate or out-of-order events. |
| `documentation-guide` | Checklist for writing technical documentation. Use when writing or updating a README, how-to guide, runbook, API docs or ADR, documenting how something works, or onboarding someone to a project. |
| `engineering-guide` | Index of my software engineering skills. Use whenever planning, building, reviewing, testing, deploying or debugging software, or preparing for tickets, calls or career decisions, to pick the relevant specialist skill(s) below, even if the task only touches one area. |
| `frontend-guide` | Checklist for building user interfaces. Use when building or reviewing UI components, managing state, fetching data in the browser, handling forms, checking accessibility or responsiveness, or improving front-end performance. |
| `how-to-work-for-me` | My working agreement for any coding or engineering task. Use whenever changing, reviewing or planning code, before making edits, to follow my rules on scope, asking first and concise communication. |
| `languages-guide` | Framework for learning and comparing programming languages. Use when picking up a new language, switching between languages, checking idioms and tooling, or building a quick-reference for a language I use. |
| `library-docs` | Check current, version-specific library documentation before writing or changing code that uses a third-party library, SDK, framework or tool (for example AWS SDK v3, Node.js, Express, Sequelize, .NET, Angular, React, Terraform providers, Kubernetes, Helm, Datadog). Uses Context7 when its MCP tools are available, otherwise the official docs on the web. Use this whenever the user asks for code, config, setup steps, upgrades or migrations involving a named library or version, says "use context7", "check the docs" or "library-docs", or when an API might have changed since training, even if they don't ask for a docs check. |
| `maintenance-guide` | Checklist for keeping software healthy over time. Use when dealing with tech debt, upgrading dependencies or runtimes, working in legacy code, removing dead code or features, or making the case for maintenance work. |
| `observability-and-debugging-guide` | Method and checklist for debugging and observability. Use when investigating a bug, error or incident, something works locally but not in production, adding logging, metrics or tracing, or when stuck on a problem and need a structured approach. |
| `performance-guide` | Checklist for finding and fixing performance problems. Use when something is slow, before optimising code, when adding caching, pagination or lazy loading, or when reviewing front-end load times or back-end latency. |
| `planning-and-requirements-guide` | Checklist for planning work and defining requirements. Use when starting a new feature, ticket or project, writing or reviewing user stories and acceptance criteria, clarifying scope, or checking whether requirements are clear enough to start building. |
| `product-thinking-guide` | Checklist for thinking about customer value and business impact. Use when deciding what to build, questioning a requirement, proposing a simpler solution, choosing success metrics, or judging whether a feature worked after release. |
| `production-readiness-guide` | Checklist for shipping and running software safely in production. Use before launching a new service or major feature, when setting up alerts, health checks or backups, planning a risky deploy, or handling an incident and postmortem. |
| `qa-test-steps-writer` | Writes QA test steps from acceptance criteria, a ticket or a PR description, in my team's format. Use whenever a ticket is moving to Ready for QA, I need to fill in BAU Test Steps, I'm asked "how should this be tested?", or I paste acceptance criteria or a change summary and need a test plan. |
| `release-ticket-writer` | Drafts a production release ticket ready for CAB, in my team's format. Use whenever I'm preparing a release, raising a Release ticket in Jira, writing release steps, rollback notes, or the Change / Reason for change / Impact summary, or bundling several tickets into one deployment. |
| `security-guide` | Security checklist for building and reviewing software. Use when handling authentication, authorisation, user input, secrets, file uploads, payments or personal data, reviewing code for vulnerabilities, or adding dependencies. |
| `snyk-remediation-workflow` | Step-by-step workflow for fixing Snyk (or npm audit) dependency vulnerabilities and writing up the ticket. Use whenever I pick up a SNYK / BAU security ticket, see a CVE or CWE in a Jira ticket, need to upgrade a vulnerable package, or write test steps for a dependency upgrade, especially for PCI-scoped services. |
| `technical-decisions-guide` | Framework for making and recording technical decisions. Use when choosing between technologies, libraries or designs, writing a technical proposal or ADR, deciding build vs buy, or justifying a recommendation to the team or stakeholders. |
| `testing-guide` | Checklist for testing strategy and writing good tests. Use when writing or reviewing tests, deciding what and how to test, fixing a bug, dealing with flaky tests, or checking whether a change is tested enough to ship. |
| `ticket-kickoff` | Before starting work on any Jira ticket, list the skills that apply and let me pick. Use whenever I share a ticket key (e.g. RDLP-1234), a Jira link, or paste ticket content and ask for help with it, even if I don't mention skills. Runs before any other ticket work. |
| `tickets-and-estimation-guide` | Checklist for writing tickets, estimating and tracking work. Use when creating or picking up a ticket, breaking down work, estimating effort, updating progress, or flagging blockers and scope changes. See planning-and-requirements-guide for stories and acceptance criteria in depth. |
| `version-control-guide` | Git reference and checklist. Use when committing, branching, merging or rebasing, writing commit messages, resolving conflicts, undoing mistakes in git, or dealing with an accidentally committed secret. |
| `ways-of-working-guide` | Checklist for working effectively in a team. Use when thinking about agile ceremonies, team communication, sharing progress, giving or receiving feedback, collaborating across teams, or improving how the team works. |

### extra-skills

Source: Trail of Bits, wshobson/agents, Karpathy, Anthropic. License: License file kept in each skill folder

| Skill | What it does |
|---|---|
| `api-design-principles` | Master REST and GraphQL API design principles to build intuitive, scalable, and maintainable APIs that delight developers. Use when designing new APIs, reviewing API specifications, or establishing API design standards. _(from wshobson/agents)_ |
| `codeql` | Scans a codebase for security vulnerabilities using CodeQL's interprocedural data flow and taint tracking analysis. Triggers on "run codeql", "codeql scan", "build codeql database", "SAST scan", "taint analysis", "dataflow analysis", or "find vulnerabilities in this repo". Covers Python, JavaScript/TypeScript, Go, Java/Kotlin, C/C++, C#, Ruby, and Swift. Supports "run all" (security-and-quality + security-experimental) and "important only" (high-precision) scan modes, and creates data extension models for project-specific sources and sinks. For fast single-file pattern matching, or when no build is available for a compiled language, use the semgrep skill; to parse SARIF that already exists rather than produce it, use the sarif-parsing skill. _(from trailofbits/skills)_ |
| `differential-review` | Performs security-focused differential review of code changes. Adapts analysis depth to codebase size, uses git blame for context, calculates blast radius by counting callers, checks test coverage of modified code, and generates a markdown report. Use when reviewing a PR, commit, or diff for security vulnerabilities, checking whether a change re-introduces a previously fixed bug, asking what else a change could break, or finding which modified code has no test covering it. _(from trailofbits/skills)_ |
| `karpathy-guidelines` | Behavioral guidelines to reduce common LLM coding mistakes. Use when writing, reviewing, or refactoring code to avoid overcomplication, make surgical changes, surface assumptions, and define verifiable success criteria. _(from forrestchang/andrej-karpathy-skills)_ |
| `mcp-server-builder` | Guide for creating high-quality MCP (Model Context Protocol) servers that enable LLMs to interact with external services through well-designed tools. Use when building MCP servers to integrate external APIs or services, whether in Python (FastMCP) or Node/TypeScript (MCP SDK). _(from anthropics/skills (renamed from mcp-builder))_ |
| `nodejs-backend-patterns` | Build production-ready Node.js backend services with Express/Fastify, implementing middleware patterns, error handling, authentication, database integration, and API design best practices. Use when creating Node.js servers, REST APIs, GraphQL backends, or microservices architectures. _(from wshobson/agents)_ |
| `sarif-parsing` | Parses and processes SARIF files from static analysis tools like CodeQL, Semgrep, or other scanners. Triggers on "parse sarif", "read scan results", "aggregate findings", "deduplicate alerts", or "process sarif output". Handles filtering, deduplication, format conversion, and CI/CD integration of SARIF data. Does NOT run scans — use the Semgrep or CodeQL skills for that. _(from trailofbits/skills)_ |
| `semgrep` | Runs a Semgrep security scan over a codebase: detects languages, selects rulesets, presents the plan for explicit approval, then runs every approved ruleset through scripts/run-scans.sh, which batches the semgrep processes and writes scans.json, and merges the output to SARIF. Supports two scan modes, "run all" for full ruleset coverage and "important only" for security findings at medium-to-high confidence and impact. Uses Semgrep Pro for cross-file taint analysis when it is available. Use when asked to scan code for vulnerabilities, run a security audit with Semgrep, find bugs, or perform static analysis. For the same scan without the approval gate, use the /static-analysis:semgrep-scan workflow. _(from trailofbits/skills)_ |
| `sharp-edges` | Identifies error-prone APIs, dangerous configurations, and footgun designs that enable security mistakes. Use when reviewing API designs, configuration schemas, cryptographic library ergonomics, or evaluating whether code follows 'secure by default' and 'pit of success' principles. Triggers: footgun, misuse-resistant, secure defaults, API usability, dangerous configuration. _(from trailofbits/skills)_ |
| `webapp-testing` | Toolkit for interacting with and testing local web applications using Playwright. Supports verifying frontend functionality, debugging UI behavior, capturing browser screenshots, and viewing browser logs. _(from anthropics/skills)_ |

### superpowers

Source: obra/superpowers (guessed from contents). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `brainstorming` | You MUST use this before any creative work - creating features, building components, adding functionality, or modifying behavior. Explores user intent, requirements and design before implementation. |
| `diagnosing-superpowers` | Use when a superpowers session went wrong and your human partner wants to know why — repeated work, ignored plans, stumbles, poor results, a skill that didn't fire, "it took too long", "why is it so expensive", "what is it doing" — or wants to build a bug report for the superpowers maintainers, for the current session or a past one identified by id or path, on any harness. |
| `dispatching-parallel-agents` | Use when facing 2+ independent tasks that can be worked on without shared state or sequential dependencies |
| `executing-plans` | Use when executing an implementation plan in the current session as the implementer yourself — your human partner chose inline execution, or no subagent tool is available |
| `finishing-a-development-branch` | Use when implementation is complete, all tests pass, and you need to decide how to integrate the work |
| `receiving-code-review` | Use when receiving code review feedback, before implementing suggestions, especially if feedback seems unclear or technically questionable - requires technical rigor and verification, not performative agreement or blind implementation |
| `requesting-code-review` | Use when completing tasks, implementing major features, or before merging to verify work meets requirements |
| `subagent-driven-development` | Use when executing implementation plans with independent tasks in the current session |
| `systematic-debugging` | Use when encountering any bug, test failure, or unexpected behavior, before proposing fixes |
| `test-driven-development` | Use when implementing any feature or bugfix, before writing implementation code |
| `using-git-worktrees` | Use when starting feature work that needs isolation from current workspace or before executing implementation plans - ensures an isolated workspace exists via native tools or git worktree fallback |
| `using-superpowers` | Use when starting any conversation - establishes how to find and use skills, requiring skill invocation before ANY response including clarifying questions |
| `verification-before-completion` | Use when about to claim work is complete, fixed, or passing, before committing or creating PRs - requires running verification commands and confirming output before making any success claims; evidence before assertions always |
| `writing-plans` | Use when you have a spec or requirements for a multi-step task, before touching code |
| `writing-skills` | Use when creating new skills, editing existing skills, or verifying skills work before deployment |

### matt-pocock-skills

Source: Matt Pocock skills (guessed). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `ask-matt` _(manual)_ | Ask which skill or flow fits your situation. A router over the skills in this repo. |
| `claude-handoff` _(manual)_ | Hand the current conversation off to a fresh background agent that picks up the work immediately. |
| `git-guardrails-claude-code` | Set up Claude Code hooks to block dangerous git commands (push, reset --hard, clean, branch -D, etc.) before they execute. Use when user wants to prevent destructive git operations, add git safety hooks, or block git push/reset in Claude Code. |
| `improve-codebase-architecture` _(manual)_ | Scan a codebase for deepening opportunities, present them as a visual HTML report, then grill through whichever one you pick. |
| `loop-me` _(manual)_ | Grill me about specs for the workflows I want to build, within this workspace. |
| `migrate-to-shoehorn` | Migrate test files from `as` type assertions to @total-typescript/shoehorn. Use when user mentions shoehorn, wants to replace `as` in tests, or needs partial test data. |
| `scaffold-exercises` | Create exercise directory structures with sections, problems, solutions, and explainers that pass linting. Use when user wants to scaffold exercises, create exercise stubs, or set up a new course section. |
| `setup-matt-pocock-skills` _(manual)_ | Configure this repo for the engineering skills: set up its issue tracker, triage label vocabulary, and domain doc layout. Run once before first use of the other engineering skills. |
| `setup-pre-commit` | Set up Husky pre-commit hooks with lint-staged (Prettier), type checking, and tests in the current repo. Use when user wants to add pre-commit hooks, set up Husky, configure lint-staged, or add commit-time formatting/typechecking/testing. |
| `setup-ts-deep-modules` _(manual)_ | Wire dependency-cruiser into a TypeScript repo so each package is a deep module, with implementation hidden in subfolders and reachable only through its entry-point files. User-invoked. |
| `wizard` | Generate an interactive bash wizard that walks a human through steps only they can perform. Use when provisioning infrastructure, setting up credentials or CI secrets, walking an unfamiliar third-party dashboard, or running a one-off migration or cutover. Don't invoke this for steps the agent can perform itself. |
| `writing-beats` _(manual)_ | Writing, exploit; assemble raw material into a journey of beats, grounding each term before a beat leans on it. |
| `writing-fragments` _(manual)_ | Writing, explore: mine raw fragments, no structure yet. |
| `writing-shape` _(manual)_ | Writing, exploit: shape raw material into an article, paragraph by paragraph. |

### supermatt-skills

Source: fork/variant of Matt Pocock skills (guessed). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `ask-supermatt` _(manual)_ | Ask which skill or flow fits your situation. A router over the skills in this repo. |
| `code-review` | Review the changes since a fixed point (commit, branch, tag, or merge-base) along three axes: Standards (does the code follow this repo's documented coding standards?), Spec (does the code match what the originating issue/spec asked for?), and Adversarial (how does the change fail in production?). Runs each axis in an independent host reader and applies the repository external-peer policy. Use when the user wants to review a branch, a PR, work-in-progress changes, or asks to "review since X". |
| `codebase-design` | Shared vocabulary for designing deep modules. Use when the user wants to design or improve a module's interface, deepen a chosen module, decide where a seam goes, make code more testable or AI-navigable, or when another skill needs the deep-module vocabulary. |
| `commit` _(manual)_ | Commit all changes on the current branch, main included. |
| `dependency-vetting` | Verify a package or tool is authentic before installing, adding, upgrading, or recommending it. Use whenever a task would add a dependency to a project, suggest a CLI tool, or pull a package from npm, PyPI, crates.io, Go modules, RubyGems, Homebrew, or any other registry. Also use when a registry page, install command, or installed artifact looks inconsistent with the project that supposedly publishes it. |
| `diagnosing-bugs` | Diagnosis loop for hard bugs and performance regressions. Use when the user says "diagnose"/"debug this", or reports something broken/throwing/failing/slow. |
| `domain-modeling` | Build and sharpen a project's domain model. Use when discussing codebase terminology, resolving a vague or overloaded word, stress-testing how domain concepts relate, writing or editing a GLOSSARY.md, or recording or editing an ADR. |
| `fix-findings` _(manual)_ | Apply every finding from the most recent review, audit, verification, or check in this session. |
| `grill-me` _(manual)_ | A relentless interview to sharpen a plan or design. |
| `grill-with-docs` _(manual)_ | A relentless interview to sharpen a plan or design, which also creates docs (ADRs and glossary) as we go. |
| `grilling` | Grill the user relentlessly about a plan, decision, or idea. Use when the user wants to stress-test their thinking, says "grill me", or asks to poke holes in, challenge, or be interviewed about a plan or design, even without the word "grill". |
| `ideate` _(manual)_ | Generate grounded ideas for what to build next, critique every one, and rank the survivors in a Markdown file. |
| `implement` _(manual)_ | Implement a piece of work based on a spec, tickets, or triaged issues. |
| `implement-spec` _(manual)_ | Implement a whole spec through parallel ticket worktrees on one integration branch. |
| `improve-architecture` _(manual)_ | Assess a codebase's architecture, stop when it is healthy, otherwise find deepening opportunities, design the chosen one, and hand a plan to /implement. |
| `improve-file-structure` _(manual)_ | Assess project file organization and prepare a behavior-preserving migration plan for /implement when reorganization is justified. |
| `improve-tests` _(manual)_ | Cut a test suite to the tests that catch real bugs and its run time to the minimum: measure first, delete or demote low-value tests, fix slow setup, and prove every cut keeps the checks that matter. |
| `jury` _(manual)_ | Put a question or decision to a jury of 3 or 5 subagents: blind independent votes, one anonymized review round, and one committed verdict with the vote, the dissent, and the first action. |
| `orchestrate` _(manual)_ | Work through GitHub issues or local Markdown tickets unattended in parallel lanes, with workers in Herdr panes and git worktrees. |
| `pr` | The shape of a pull request body: a summary diagram, before/after evidence, and merge danger. Use when opening a PR, writing or rewriting a PR description, or when another flow needs a PR body. |
| `prototype` | Build a throwaway prototype to answer a design question. Use when the user wants to sanity-check whether a state model or logic feels right, or explore what a UI should look like. |
| `qa` | QA a change in the running program, the way its user meets it: drive a CLI or terminal UI through tmux, a web app through a browser, and check every requested behavior against what you observe. Use after implementing a change and before code review, or when the user asks for a QA pass, a smoke test, or a click-through of a change, or asks whether it actually works. |
| `refactor` _(manual)_ | Refactor code at method, file, or project scope. Assesses first and stops when the code is already clean, routes architecture problems elsewhere, and gates edits on test coverage. Language-agnostic. |
| `research` | Investigate a question against high-trust primary sources and capture the findings as a Markdown file in the repo. Use when the user wants a topic researched, docs or API facts gathered, or reading legwork delegated to a background agent. |
| `resolving-merge-conflicts` | Resolves an in-progress git merge or rebase conflict by tracing why each side changed, reconciling every conflicted hunk, running the project's checks, and finishing the merge or rebase. Use when a merge, rebase, or pull stops on conflicts, when files contain conflict markers, or when the user asks to fix or resolve merge conflicts. |
| `retro` _(manual)_ | Conduct a retrospective on a coding session. |
| `setup-supermatt-skills` _(manual)_ | Configure this repo for the engineering skills: set up its issue tracker, triage labels, domain doc layout, and external peer policy. Run once before first use of the other engineering skills. |
| `ship-pr` _(manual)_ | Commit, push, open a pull request, repair CI within bounded attempts, then squash merge and verify post-merge workflows. |
| `tdd` | Test-driven development. Use when the user wants to build features or fix bugs test-first, mentions "red-green-refactor", or wants integration tests. |
| `teach` _(manual)_ | Teach the user a new skill or concept, within this workspace. |
| `to-questionnaire` _(manual)_ | Turn a decision you can't fully answer into a questionnaire for someone else to fill in. |
| `to-spec` _(manual)_ | Turn the current conversation into a spec and publish it to the project issue tracker: no interview, just synthesis of what you've already discussed. |
| `to-tickets` _(manual)_ | Break a plan, spec, or the current conversation into a set of tracer-bullet tickets, each declaring its blocking edges, published to the configured tracker (edges as text in one file per ticket locally, or native blocking links on a real tracker). |
| `triage` _(manual)_ | Move issues and external PRs through a state machine of triage roles, categorise, verify, grill if needed, and write agent-ready briefs. |
| `wait-what` _(manual)_ | Stop. That last message did not land: re-pitch it. |
| `wayfinder` _(manual)_ | Plan a huge chunk of work (more than one agent session can hold) as a shared map of decision tickets on your issue tracker, and resolve them one at a time until the way to the destination is clear. |
| `what-would-you-do` _(manual)_ | Explain the question you just asked and recommend an answer, with the case for and against each option. |
| `writing-for-agents` | Writing documents for agents. Use when creating or editing skills, modifying AGENTS.md or CLAUDE.md, or writing any doc an agent reaches by a pointer. |

### engineering-team-roles

Source: 10x-team role pack (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `10x-team` | You MUST use this when building projects end-to-end. Orchestrates all 12 team roles — automatically switches between CTO, architect, PM, engineers, SRE, security, DBA, QA, and EM based on the current phase of work. Starts with brainstorming before any implementation. |
| `cto` | You MUST use this for strategic technology decisions - build vs buy, architecture direction, resource allocation, technical vision, risk assessment. Evaluates decisions at the intersection of business and technology. |
| `dba` | You MUST use this for database decisions - schema design, query optimization, migration planning, indexing strategy, data modeling, and database performance issues. |
| `devops-engineer` | You MUST use this for infrastructure and deployment decisions - CI/CD pipelines, containerization, IaC, deployment strategies, environment management, and build automation. |
| `engineering-manager` | You MUST use this for team and process decisions - sprint planning, team structure, delivery estimation, process improvements, technical hiring, and engineering team operations. |
| `init-project` | _No description in SKILL.md._ |
| `principal-architect` | You MUST use this for system design and architecture decisions - designing systems, choosing patterns, defining boundaries, data modeling, and making structural decisions that are hard to change later. |
| `product-manager` | You MUST use this for product decisions - feature prioritization, user stories, roadmap planning, requirement gathering, and defining what to build and why. |
| `qa-engineer` | You MUST use this for testing and quality decisions - test strategy, test plans, bug analysis, testing frameworks, coverage gaps, and quality assurance processes. |
| `sde` | You MUST use this for hands-on coding tasks - writing features, fixing bugs, implementing APIs, debugging issues, and writing clean production code. |
| `security-engineer` | You MUST use this for security decisions - threat modeling, vulnerability assessment, auth/authz design, security review, compliance requirements, and hardening recommendations. |
| `senior-engineer` | You MUST use this for implementation guidance - code review, design patterns, debugging complex issues, writing production-quality code, and mentoring on engineering best practices. |
| `sre` | You MUST use this for reliability and operations decisions - incident response, monitoring, SLOs, capacity planning, performance debugging, and production reliability. |
| `staff-engineer` | You MUST use this for cross-cutting technical decisions - code quality standards, cross-team patterns, technical debt strategy, mentoring on complex problems, and driving alignment on engineering practices. |

### backend-discipline

Source: senior backend discipline pack (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `audit` | Audit an existing backend component (endpoint, worker, consumer, CLI, integration, cron) against senior discipline. Checks invariants, error handling, idempotence, authorization, and observability. |
| `auth-and-authorization` | Use when designing or modifying any auth flow, permission check, session, token issuance, multi-tenant data scope, or admin path. Forces explicit separation of authentication and authorization, decisions about enforcement layers, and treatment of tokens as bearer credentials. Apply this whenever you add an endpoint, a role, a scope, or a tenant boundary. |
| `boring-by-default` | Use when choosing a database, queue, language, deployment shape, auth scheme, or any infrastructure piece. Forces a defense of complexity before adopting new technology. Reach for this whenever the answer involves "let's use" followed by a name you read on Hacker News this month. |
| `data-modeling-discipline` | Use whenever creating or changing a database schema, defining an entity, writing an ORM model, or designing a data structure that will be persisted. Forces invariants into the schema instead of trusting the application layer. Use this BEFORE writing the migration. |
| `debugging-discipline` | Use when the user reports something broken, slow, flaky, or wrong in production or staging ("it's slow", "it crashes", "it doesn't work", "we're seeing 500s", "the data is wrong"). Forces an investigation method instead of guessing. Apply BEFORE proposing a fix. Mandatory the moment someone says "in prod". |
| `design` | Design a backend component (endpoint, worker, CLI, script, consumer, cron, integration) using the senior 6-step workflow before writing any code. |
| `error-handling-as-design` | Use when designing or implementing any backend component, BEFORE the happy path. Treats the error path as part of the contract, not as cleanup. Catches the silent swallow, the bare except, the wrapped-and-lost stack trace, and the generic 500. Apply this whenever you reach for try/catch. |
| `explain-this-query` | Analyze a SQL query (or ORM call) for likely execution plan, missing indexes, and risks BEFORE it ships. Predicts EXPLAIN-style output and flags concerns. |
| `hunt-n-plus-one` | Scan code for likely N+1 query patterns and propose fixes. Works across ORMs (Prisma, SQLAlchemy, ActiveRecord, TypeORM, Django, Sequelize, GORM, etc.) and raw SQL inside loops. |
| `idempotency-and-side-effects` | Use when designing any operation that changes state, sends a message, makes a payment, calls a third party, emits an event, or writes to multiple stores. Forces idempotence and the outbox pattern so replays and retries never duplicate side effects. Apply this BEFORE writing the handler, job, or consumer. |
| `migration-safety` | Use whenever writing, reviewing, or running a database migration (SQL files, ORM migrations, schema changes). Every migration is a potential incident. This skill catches the patterns that cause production lock-ups, partial deploys, and irreversible damage BEFORE the file ships. |
| `observability-by-default` | Use when building or modifying any backend component (endpoint, worker, consumer, CLI, cron, daemon), BEFORE the code ships. Forces structured logs, RED metrics, trace IDs, and real healthchecks so the component can be debugged at 3am without SSH. If you wrote a service-side component without this, it is not done. |
| `performance-and-scaling` | Use when building or modifying any backend component, BEFORE making perf or scaling choices. Forces the question "at what load" up front, names the bottleneck axis, and pushes vertical scaling and indexes before distributed anything. Apply this whenever you are tempted to "make it fast" without numbers, or to "make it scale" before measuring. |
| `query-discipline` | Use when writing, reviewing, or generating any database query (raw SQL, ORM call, query builder). Catches N+1, missing indexes, unbounded lists, and bad pagination BEFORE the query reaches production. Use this whenever you reach for an ORM or write a SELECT. |
| `review-migration` | Review a database migration against senior backend discipline. Flags lock-up risks, irreversibilities, and missing-deprecation patterns BEFORE the file is committed. |
| `security-discipline` | Use on every diff, every new endpoint, every change to a backend component. Treats security as a per-change reflex, not an audit phase. Catches IDOR/BOLA, mass assignment, injection, secret leaks, missing auth, and the everyday holes that ship while nobody is looking at "security". Apply this BEFORE marking a change as done. |
| `testing-with-discernment` | Use when writing, reviewing, or planning tests for any backend code. Forces a "what is worth testing" decision instead of a coverage target. Catches tests that mock the code they claim to test, tests that pass even when the feature is broken, and snapshot tests pretending to be assertions. Apply whenever you are tempted to write a test, and BEFORE marking a bug fix done. |
| `think-before-coding` | Use BEFORE writing any backend code (endpoint, worker, CLI, script, consumer, cron, pipeline, daemon, webhook handler, integration). Forces the 6-step senior workflow so the design is sound before the first line ships. If you are about to write a server-side component of any kind, you MUST invoke this first. |

### sanity

Source: Sanity (guessed from contents). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `content-experimentation-best-practices` | Content experimentation and A/B testing guidance covering experiment design, hypotheses, metrics, sample size, statistical foundations, CMS-managed variants, and common analysis pitfalls. Use this skill when planning experiments, setting up variants, choosing success metrics, interpreting statistical results, or building experimentation workflows in a CMS or frontend stack. |
| `content-modeling-best-practices` | Structured content modeling guidance for schema design, content architecture, content reuse, references versus embedded objects, separation of concerns, and taxonomies across Sanity and other headless CMSes. Use this skill when designing or refactoring content types, deciding field shapes, debating reusable versus nested content, planning omnichannel content models, or reviewing whether a schema is too page-shaped or presentation-driven. |
| `deploy-schema` | Deploy Sanity schema to the Content Lake with verification. |
| `portable-text-conversion` | Convert HTML and Markdown content into Portable Text blocks for Sanity. Use when migrating content from legacy CMSs, importing HTML or Markdown into Sanity, building content pipelines that ingest external content, converting rich text between formats, or programmatically creating Portable Text documents. Covers @portabletext/markdown (markdownToPortableText), @portabletext/block-tools (htmlToBlocks), custom deserializers, and the Portable Text specification for manual block construction. |
| `portable-text-serialization` | Render and serialize Portable Text to React, Svelte, Vue, Astro, HTML, Markdown, and plain text. Use when implementing Portable Text rendering in any frontend framework, building custom serializers for non-standard block types, converting Portable Text to HTML strings server-side, converting Portable Text to Markdown, extracting plain text from Portable Text, or troubleshooting rendering issues with marks, blocks, lists, or custom types. |
| `sanity` | Lists available Sanity skills and help topics. |
| `sanity-best-practices` | Sanity development best practices for schema design, GROQ queries, TypeGen, Visual Editing, images, Portable Text, Studio structure, localization, migrations, Sanity Functions, webhooks, Blueprints, and framework integrations such as Next.js, Nuxt, Astro, Remix, SvelteKit, Angular, Hydrogen, and the App SDK. Use this skill whenever working with Sanity schemas, defineType or defineField, GROQ or defineQuery, content modeling, Presentation or preview setups, Sanity-powered frontend integrations, event-driven content automation, documentEventHandler, defineDocumentFunction, defineMediaLibraryAssetFunction, @sanity/functions, @sanity/blueprints, sanity.blueprint.ts, event-driven content automation, or when reviewing and fixing a Sanity codebase. |
| `sanity-migration` | Plans, implements, and reviews migrations from other CMSes and content systems into Sanity. Use when migrating or replatforming to Sanity from AEM, Adobe Experience Manager, Contentful, Strapi, Webflow, WordPress, Payload, Drupal, Markdown/MDX/frontmatter files, WXR/XML exports, CMS APIs, database dumps, static HTML, or when designing extraction, transformation, Portable Text conversion, asset migration, redirects, validation, and cutover workflows. |
| `sanity-review` | Review code for Sanity best practices and common issues. |
| `seo-aeo-best-practices` | SEO and AEO best practices for metadata, Open Graph, sitemaps, robots.txt, hreflang, JSON-LD structured data, EEAT, and content optimized for search engines and AI answer surfaces. Use this skill when implementing page SEO, technical SEO, schema markup, international SEO, AI-overview readiness, or improving content for Google, ChatGPT, Perplexity, and similar assistants. |
| `typegen` | Run Sanity TypeGen and troubleshoot type generation issues. |

### engineering-workflows

Source: engineering workflow pack (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `architecture` | Create or evaluate an architecture decision record (ADR). Use when choosing between technologies (e.g., Kafka vs SQS), documenting a design decision with trade-offs and consequences, reviewing a system design proposal, or designing a new component from requirements and constraints. |
| `debug` | Structured debugging session — reproduce, isolate, diagnose, and fix. Trigger with an error message or stack trace, "this works in staging but not prod", "something broke after the deploy", or when behavior diverges from expected and the cause isn't obvious. |
| `deploy-checklist` | Pre-deployment verification checklist. Use when about to ship a release, deploying a change with database migrations or feature flags, verifying CI status and approvals before going to production, or documenting rollback triggers ahead of time. |
| `documentation` | Write and maintain technical documentation. Trigger with "write docs for", "document this", "create a README", "write a runbook", "onboarding guide", or when the user needs help with any form of technical writing — API docs, architecture docs, or operational runbooks. |
| `incident-response` | Run an incident response workflow — triage, communicate, and write postmortem. Trigger with "we have an incident", "production is down", an alert that needs severity assessment, a status update mid-incident, or when writing a blameless postmortem after resolution. |
| `standup` | Generate a standup update from recent activity. Use when preparing for daily standup, summarizing yesterday's commits and PRs and ticket moves, formatting work into yesterday/today/blockers, or structuring a few rough notes into a shareable update. |
| `system-design` | Design systems, services, and architectures. Trigger with "design a system for", "how should we architect", "system design for", "what's the right architecture for", or when the user needs help with API design, data modeling, or service boundaries. |
| `tech-debt` | Identify, categorize, and prioritize technical debt. Trigger with "tech debt", "technical debt audit", "what should we refactor", "code health", or when the user asks about code quality, refactoring priorities, or maintenance backlog. |
| `testing-strategy` | Design test strategies and test plans. Trigger with "how should we test", "test strategy for", "write tests for", "test plan", "what tests do we need", or when the user needs help with testing approaches, coverage, or test architecture. |

### data-analysis

Source: data analysis pack (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `analyze` | Answer data questions -- from quick lookups to full analyses. Use when looking up a single metric, investigating what's driving a trend or drop, comparing segments over time, or preparing a formal data report for stakeholders. |
| `build-dashboard` | Build an interactive HTML dashboard with charts, filters, and tables. Use when creating an executive overview with KPI cards, turning query results into a shareable self-contained report, building a team monitoring snapshot, or needing multiple charts with filters in one browser-openable file. |
| `create-viz` | Create publication-quality visualizations with Python. Use when turning query results or a DataFrame into a chart, selecting the right chart type for a trend or comparison, generating a plot for a report or presentation, or needing an interactive chart with hover and zoom. |
| `data-context-extractor` | Generate or improve a company-specific data analysis skill by extracting tribal knowledge from analysts. BOOTSTRAP MODE - Triggers: "Create a data context skill", "Set up data analysis for our warehouse", "Help me create a skill for our database", "Generate a data skill for [company]" → Discovers schemas, asks key questions, generates initial skill with reference files ITERATION MODE - Triggers: "Add context about [domain]", "The skill needs more info about [topic]", "Update the data skill with [metrics/tables/terminology]", "Improve the [domain] reference" → Loads existing skill, asks targeted questions, appends/updates reference files Use when data analysts want Claude to understand their company's specific data warehouse, terminology, metrics definitions, and common query patterns. |
| `data-visualization` | Create effective data visualizations with Python (matplotlib, seaborn, plotly). Use when building charts, choosing the right chart type for a dataset, creating publication-quality figures, or applying design principles like accessibility and color theory. |
| `explore-data` | Profile and explore a dataset to understand its shape, quality, and patterns. Use when encountering a new table or file, checking null rates and column distributions, spotting data quality issues like duplicates or suspicious values, or deciding which dimensions and metrics to analyze. |
| `sql-queries` | Write correct, performant SQL across all major data warehouse dialects (Snowflake, BigQuery, Databricks, PostgreSQL, etc.). Use when writing queries, optimizing slow SQL, translating between dialects, or building complex analytical queries with CTEs, window functions, or aggregations. |
| `statistical-analysis` | Apply statistical methods including descriptive stats, trend analysis, outlier detection, and hypothesis testing. Use when analyzing distributions, testing for significance, detecting anomalies, computing correlations, or interpreting statistical results. |
| `validate-data` | QA an analysis before sharing -- methodology, accuracy, and bias checks. Use when reviewing an analysis before a stakeholder presentation, spot-checking calculations and aggregation logic, verifying a SQL query's results look right, or assessing whether conclusions are actually supported by the data. |
| `write-query` | Write optimized SQL for your dialect with best practices. Use when translating a natural-language data need into SQL, building a multi-CTE query with joins and aggregations, optimizing a query against a large partitioned table, or getting dialect-specific syntax for Snowflake, BigQuery, Postgres, etc. |

### design

Source: design pack (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `accessibility-review` | Run a WCAG 2.1 AA accessibility audit on a design or page. Trigger with "audit accessibility", "check a11y", "is this accessible?", or when reviewing a design for color contrast, keyboard navigation, touch target size, or screen reader behavior before handoff. |
| `design-critique` | Get structured design feedback on usability, hierarchy, and consistency. Trigger with "review this design", "critique this mockup", "what do you think of this screen?", or when sharing a Figma link or screenshot for feedback at any stage from exploration to final polish. |
| `design-handoff` | Generate developer handoff specs from a design. Use when a design is ready for engineering and needs a spec sheet covering layout, design tokens, component props, interaction states, responsive breakpoints, edge cases, and animation details. |
| `design-system` | Audit, document, or extend your design system. Use when checking for naming inconsistencies or hardcoded values across components, writing documentation for a component's variants, states, and accessibility notes, or designing a new pattern that fits the existing system. |
| `research-synthesis` | Synthesize user research into themes, insights, and recommendations. Use when you have interview transcripts, survey results, usability test notes, support tickets, or NPS responses that need to be distilled into patterns, user segments, and prioritized next steps. |
| `user-research` | Plan, conduct, and synthesize user research. Trigger with "user research plan", "interview guide", "usability test", "survey design", "research questions", or when the user needs help with any aspect of understanding their users through research. |
| `ux-copy` | Write or review UX copy — microcopy, error messages, empty states, CTAs. Trigger with "write copy for", "what should this button say?", "review this error message", or when naming a CTA, wording a confirmation dialog, filling an empty state, or writing onboarding text. |

### workflow-studio

Source: full-stack workflow pack, Vue/Tabler flavoured (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `adversarial-review` | Run several independent model seats against one problem or one plan, make them attack each other, fact-check every contested claim, then ask the human one gate of questions. Two modes: a design panel for an open problem, and a plan review for a drafted or approved plan. Use only when the human asks for adversarial or multi-seat work. Not for a code diff (use /code-review), pure ideation (idea-refine), or a single Verifier pass on one claim. |
| `app-store` | App Store and Google Play listings: title, subtitle, keywords, description, screenshots, previews, ratings prompts. Use when preparing or auditing a store listing or asking why installs are low. Copy wording is plain-language; visuals are design-assets; pricing is marketing. |
| `code-quality` | Standards for reviewing and cleaning up code. Use when reviewing any diff (your own before commit, a Codex or sub-agent diff, a colleague's PR) or when asked to clean up, de-duplicate or delete dead code. Holds the hard rules, the review checklist (standards and spec axes), module-design tests, and proof of deadness before deleting. To run a review use /code-review; to apply cleanups, /simplify. |
| `data-analytics` | Decide which metrics, KPIs and charts an app's data deserves. Use when exploring a schema or domain, planning a dashboard ("what should this show?", "add stats to X"), or choosing which data points matter. Keeps a per-project catalog. Query speed is database-optimization; chart UI is frontend; chart colors are design-guide. |
| `database-optimization` | Correct, fast queries, views, indexes and schema. Use before adding or changing any query (ORM or raw), entity, migration, index or view, and when an endpoint or list is slow. In a TypeORM project, load it before writing ORM code. Which service owns a table is service-architecture; running migrations locally is project-config. |
| `debugging-and-error-recovery` | Root-cause debugging. Use when a test fails, a build breaks, behavior doesn't match expectations, or any unexpected error appears. Builds a loop that goes red on the failure before theorising, ranks falsifiable hypotheses, and ends with a regression test. |
| `deprecation-and-migration` | Remove or replace systems, APIs and features. Use when sunsetting code, migrating users to a new implementation, running a strangler migration off a legacy service, or making an expand/contract schema change while old and new code share one database. |
| `design-assets` | Visual assets: logos, icons, illustrations, hero and OG images, empty-state art, favicons, raster-to-vector conversion. Use whenever a task needs one. Recraft is called first and hand-authoring is the fallback; covers the art-direction brief and integration. Visual judgment is design-guide. |
| `design-guide` | Visual and UX judgment: color, typography, spacing, hierarchy, themes. Use when choosing colors or status/badge colors, theming (white-label included), making a screen "look better" or more polished, or reviewing a UI's visual quality. Decides how it looks; structure is frontend, Tabler specifics are tabler-ui, content placement is information-architecture. |
| `done` | Session close-out with no resume prompt. Use on /done, or when wrapping up a session where nothing remains to resume or the continuation prompt already exists (a standup queue's next item). Runs the handoff close-out minus the resume-prompt step. Need a fresh resume prompt? Use handoff instead, never both. In a parent session it closes the child sessions first. |
| `explain` _(manual)_ | Re-explain the last message in plain words, using the project's own vocabulary. |
| `find-skills` | Discover and install agent skills. Use only when the user explicitly asks for a skill ("find or install a skill for X", "is there a skill that..."), never for an ordinary how-do-I question. |
| `first-customers` | Find and reach a product's first customers honestly: demand signals, local-business prospect lists, outreach drafts a human sends. Use when asking "who would buy this" or "how do I get my first users or clients". Offer and positioning are marketing; wording is plain-language. |
| `frontend` | Frontend structure and behavior: components, state, a typed service layer, lists, tables and filters, forms, modals, loading/empty/error states, routing, SSR, web performance. Use when building or refactoring UI or adding any screen. Vue 3 + Tabler today, framework-agnostic in approach. Tabler specifics are tabler-ui; visual judgment is design-guide; content placement is information-architecture. |
| `git-sync` | The standing git workflow. Use at the start of any branch work and before every commit, push, rebase or PR: your own branch (never main), rebased on current main, every branch pushed, PR bodies in the standard shape, PRs reported only when green, and merged branches and worktrees pruned before a session ends. |
| `grant-writing` | Research grant applications: research and mentoring plans, specific aims, budget justifications, abstracts. Use when writing or strengthening a proposal, checking a draft against a funder's guidelines or review criteria, or responding to reviewers. Owns proposal strategy and structure; wording is academic-writing, study design is research-methods. |
| `handoff` | Durable session handoff with a resume prompt. Use when pausing or ending work at a real boundary (a phase or PR done, a blocker, a pivot, a drained queue) or when the user says "hand off" or "we'll continue later". Saves state outside the chat plus an exact resume point, never just a chat summary. No new resume prompt needed? Use done. |
| `i18n` | Multi-language support (i18n/l10n). Use when a task touches a translation file or a user-facing string in a product that ships more than one language: adding a language or key, extracting strings, vue-i18n/nestjs-i18n/go-i18n, locale formatting, translated data (enums, emails, PDFs), locale routing, hreflang, RTL. Its core failure is a key that reaches one pack and not the others. |
| `idea-refine` | Turn a vague idea into a sharp, actionable concept by diverging, then converging. Use for pure ideation: "ideate", "refine this idea", "explore options for X". It sits upstream of a plan; to plan an idea already chosen, use planning. |
| `information-architecture` | How content and pages are organized for their audience: site maps, page inventories, each page's job, where a message or feature lives, navigation and funnels, heading structure, buried or orphaned messages. Applies to docs, books, curricula and papers too. Use when outlining, when adding or reordering pages or sections, and on any content-page review. Looks are design-guide; wording is plain-language or academic-writing. |
| `infrastructure` | Change infrastructure and dev-workflow tooling: Nomad, Consul, Vault, Terraform, Docker, GitHub Actions, task runners, env and direnv setup, setup scripts, a project's own ops CLI, launchd and hooks. Use when editing any of these or debugging env or worktree setup. Looking up how to run a project is project-config; third-party APIs are integrations. |
| `integrations` | Connect to or automate third-party services: REST APIs, MCP servers, OAuth and tokens, webhooks, recurring syncs. Use when building or debugging an integration, scheduling a job against an external service, deciding where automation runs, making external writes idempotent, or researching a vendor API. Internal service-to-service calls are service-architecture. |
| `marketing` | Why people choose, buy, sign up and stay, applied honestly: behavioral models, offers, pricing, trust, urgency, onboarding and growth loops for the apps and sites we build. Use when shaping a landing, pricing, signup or launch page, an offer or free tier, or asking "why would anyone pick this". Wording is plain-language; page structure is information-architecture. |
| `monitoring` | Observability into running code. Use when adding logging or instrumentation, diagnosing a running service ("watch the logs", "what is it actually doing"), standardizing log output, or when a change must be proven on the live app because tests can't reach it. Deploy and alerting stacks are infrastructure; tests are tdd-skill. |
| `orchestration` | Run multi-step or long-running work as an orchestrator over disposable sub-agents. Use at the start of a program phase, migration, broad sweep, deep research or many-file job, or when your context fills with exploration. Not for single-step edits or quick questions. |
| `plain-language` | Clear, friendly, jargon-free writing for non-technical readers: ticket text, QA steps, release notes, status updates, UI copy, business messages. Use when writing for QA, product, stakeholders or end users, or on a "make this less technical" pass. Scholarly prose is academic-writing; document structure is information-architecture. |
| `planning` | Plan before building anything non-trivial: multi-file or multi-phase work, a feature, a migration, or whenever asked to plan. Research, write the plan, ask every decision up front (a second gate only for questions that depend on a first-gate answer), get approval, then execute autonomously. No implementation while the approval gate is open. |
| `project-config` | The recorded facts of how each project runs: node version, env and direnv, package manager, monorepo layout, and the exact install, run, build, test, lint and migrate commands. Consult before your first shell command in a repo and before briefing an agent that will run one. Record any missing fact the moment you find it. |
| `project-manager` | Keep the tracker (Jira, Trello, or GitHub Issues and Projects) in sync with the real work. Use on /project-manager or "file a ticket", "is this tracked", "write QA steps", "audit my tickets", "find duplicates", "clean up the backlog". Drafts every change and asks before writing to the tracker. Working your assigned tickets is standup. |
| `research-methods` | Social and health research design: conceptual and logic models, CBPR/YPAR, participatory and agent-based modeling, spatial indices, implementation frameworks (CFIR, RE-AIM), measures, IRB and human-subjects sections, literature synthesis. Use when planning a study or choosing a method or framework. Proposal structure is grant-writing; wording is academic-writing. |
| `security-and-hardening` | Security standards a default pass gets wrong: credential reach, proving a control holds, leak-free secret scanning, SSRF/TOCTOU, deployment topology. Use when handling untrusted input, auth, sessions, stored data or third-party calls; adding or upgrading a dependency; pinning Actions or base images; editing CI, Dockerfiles or hooks; wiring an MCP server; or when the secret-scan hook denies a commit. Run the review itself with /security-review. |
| `service-architecture` | Backend architecture decisions: service boundaries, splitting vs consolidating, inter-service calls, auth guards and tiers, where logic lives, strangler migrations. Load before adding or versioning an endpoint or a service-to-service call, or deciding which service owns something. Query performance is database-optimization. |
| `source-driven-development` | Ground implementation decisions in official documentation, with citations. Use when building with a framework or library where correctness matters or common patterns may be outdated. |
| `status-update` | Session status as a visual dashboard plus a 2-3 line TLDR, never prose alone. Use on /status-update, "where are we", "what's left", mid-way through a multi-item run, and at any wrap-up covering more than one unit of work. |
| `tabler-ui` | Tabler admin template (tabler.io) components and the workarounds that make them behave in Vue 3. Consult before any Tabler markup or interactive component: modals, dropdowns, badges, grids, forms, icons, wizards, empty states, emails. Structure is frontend; visual judgment is design-guide. |
| `tdd-skill` | Test-first (red-green-refactor) for any codebase. Use when adding or changing behavior, fixing a bug (it starts with a failing regression test), or asked to add or cover tests. Finds how this project runs tests, names the seams under test, and verifies on a live stack when a unit test can't reach the behavior. Watching an existing change run is /verify. |

### productivity

Source: productivity pack (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `memory-management` | Two-tier memory system that makes Claude a true workplace collaborator. Decodes shorthand, acronyms, nicknames, and internal language so Claude understands requests like a colleague would. CLAUDE.md for working memory, memory/ directory for the full knowledge base. |
| `start` | Initialize the productivity system and open the dashboard. Use when setting up the plugin for the first time, bootstrapping working memory from your existing task list, or decoding the shorthand (nicknames, acronyms, project codenames) you use in your todos. |
| `task-management` | Simple task management using a shared TASKS.md file. Reference this when the user asks about their tasks, wants to add/complete tasks, or needs help tracking commitments. |
| `update` | Sync tasks and refresh memory from your current activity. Use when pulling new assignments from your project tracker into TASKS.md, triaging stale or overdue tasks, filling memory gaps for unknown people or projects, or running a comprehensive scan to catch todos buried in chat and email. |

### security-scanner

Source: Claude Security menu plugin (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `claude-security` _(manual)_ | The Claude Security menu — pick a job: scan the codebase (the whole repository or a scoped part of it), scan changes (this branch's or a pull request's diff, or one commit), or suggest patches (findings turned into targeted patch files, each verified by a panel of agents, that you apply when you choose). |

### cv-builder

Source: CV Builder plugin (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `create-resume` | Draft a new resume from the user's facts as canonical cv-builder/v1 Markdown. Use when the user asks to create, write, or build a resume or CV from scratch (English, Russian or Japanese), optionally filling a shipped CV Builder skeleton and handing the result to the browser-based CV Builder through the open_builder MCP tool. |
| `review-resume` | Review a resume's content, structure, and ATS safety using the same criteria as the CV Builder's preflight. Use when the user asks to review, critique, check, or give feedback on a resume or CV. |
| `rewrite-achievements` | Rewrite resume bullets or entries into action-result form with honest quantification. Use when the user asks to improve, strengthen, or rewrite experience bullets, achievements, or role descriptions. |
| `tailor-resume` | Adapt an existing resume to a target job posting without inventing facts: assess fit, map truthful keywords, flag gaps, and deliver canonical cv-builder/v1 Markdown. Use when the user provides a resume (cv-builder/v1 Markdown or plain text) plus a vacancy or job description and asks to tailor, target, or adjust the resume to it. |

### ai-mentor

Source: AI workflow mentor plugin (unknown author). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `mentor` | Match a developer's question or problem to the best AI workflow, ranked and personalized from a persistent profile of what they already know. MUST BE USED — instead of answering from general knowledge — whenever the user asks how to approach a task with AI or Claude ("how should I approach...", "what's the best way to use AI/Claude for...", "is there a smarter way to..."), which workflow or capability fits their task, or how to be more productive with AI tools. This skill's verified catalog, repo grounding, and user profile produce a strictly better answer than a direct reply. |

### caveman

Source: caveman (guessed JuliusBrussee/caveman). License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `caveman` | Use this skill whenever the user says "caveman mode", "caveman", "talk like caveman", "speak simple", "dumb it down", "ELI5 caveman", or asks to switch to short/simple talk. Also use this skill when the user has asked for caveman style earlier in the session and has not turned it off. Switches all replies to short, blunt, caveman-style sentences with small words. |

### humanizer

Source: humanizer pack. License: License file bundled.

| Skill | What it does |
|---|---|
| `humanizer` | Rewrite AI-sounding text so it reads like the writer without changing what it says. Use when editing or reviewing prose for AI tells: not-X-but-Y contrasts, one-line closers, staged openers, forced triads, dashes everywhere, inflated claims, sales language, stock AI words, bold labels, or filler. Based on Wikipedia's "Signs of AI writing." |

### modern-web-guidance

Source: modern-web-guidance plugin. License: Unknown, not bundled.

| Skill | What it does |
|---|---|
| `chrome-extensions` | Build and publish Chrome Extensions using Manifest V3 best practices. Use this skill whenever the user asks to create, modify, debug, or understand Chrome browser extensions, add-ons, or anything involving the Chrome Extensions API. Trigger on mentions of: 'Chrome extension', 'browser extension', 'manifest.json', 'content script', 'service worker' (in browser context), 'popup' (in browser extension context), 'side panel', 'chrome.* API', 'declarativeNetRequest', 'omnibox', 'context menu' (in extension context), 'userScripts', 'user script', 'script manager', or any request to build functionality that integrates with the Chrome browser UI. Also trigger for publishing to the Chrome Web Store: 'publish extension', preparing an extension for publishing, responding to a review rejection, writing permission justifications, or drafting a privacy policy. |
| `modern-web-guidance` | Search tool for modern web development best practices. MANDATORY: Execute FIRST for all HTML/CSS and clientside JS tasks. Do NOT skip — web APIs evolve rapidly and training weights contain obsolete patterns. Trigger immediately for: - UI/Layout: Modals, dialogs, popovers, Glassmorphism/backdrop-filters, anchor positioning, container queries, `:has()`, `:user-valid`. - Scroll/Motion: View Transitions, Scroll-driven animations, scroll parallax/reveals. - Performance: CWV (LCP, INP), content-visibility, Fetch Priority, image optimization. - System/APIs: Local filesystem access, WebUSB, WebSockets sync, WebAssembly widgets. - Frameworks: Adapting layout/styles in React, Vue, Angular. - General Frontend: Forms, autofill, advanced inputs, custom scrollbars, modern component states, etc. DO NOT trigger for: - Backend: Database SQL, ORMs, Express API routes. - Pipelines: CI/CD deployment, Docker, Actions. - Generic: Local scripts (Python/Go tools), ESLint, Git. |

### datadog

Source: Datadog plugin. License: Unknown, not bundled. Needs the Datadog MCP server to work.

| Skill | What it does |
|---|---|
| `datadog-app` | Use ONLY when the user explicitly asks to create, scaffold, or initialize a new Datadog App project — they must use action words like "create", "scaffold", "new", or "build" together with "Datadog App" or "@datadog/apps" or "npm create @datadog/apps". Do NOT use for any question that does not involve creating a new project from scratch — questions about Datadog observability products (logs, metrics, APM, traces, monitors, dashboards), working inside an existing project, deploying, publishing, auth, or CI/CD. |
| `ddconfig` | Configures or troubleshoots the plugin's Datadog MCP server. Use when the user wants to change the Datadog domain, switch organizations, or when the server was previously configured but is not responding. |
| `ddsetup` | First-time initialization of the plugin's Datadog MCP server. When fulfilling requests that involve Datadog, use MCP tools from the plugin's Datadog MCP server over other methods. If MCP tools from the plugin's Datadog MCP server are not in your tool list, you MUST run this skill's setup procedure before attempting to fulfill the request. Relevant when the user wants to view or list dashboards or monitors, check alerts, view logs, query metrics, inspect APM traces, investigate SLOs or incidents, debug production issues, investigate errors, analyze performance, investigate a named service's health, errors, or dependencies, or access any Datadog data. |
| `ddtoolsets` | Manages toolsets for the plugin's Datadog MCP server. Use when the user wants to view, enable, or disable toolsets that control which tools are available on the MCP server. |
| `ddviz` | Enables, disables, or reports the status of the Datadog visualization panel (ddviz). macOS only. Use when the user wants to turn ddviz on or off, or check whether it's currently enabled. |
