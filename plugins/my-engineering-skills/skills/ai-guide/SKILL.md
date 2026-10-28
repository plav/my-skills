---
name: ai-guide
description: Checklist for using AI in engineering work and building AI features. Use when prompting AI tools, setting up Claude Code with CLAUDE.md, skills, hooks or MCP, reviewing AI-generated code, building features that call an LLM, or writing evals.
---

# AI

## Checklist
- Clear prompt: context, goal, constraints, examples, output format
- Right context given (files, docs, conventions)
- AI output verified: run it, test it, check against docs
- AI-generated code reviewed for security and maintainability
- No sensitive or customer data in prompts; follow company policy
- Human review for consequential changes

## Prompting
- Be specific; say what good looks like
- Give examples (good and bad)
- Ask for step-by-step reasoning on complex tasks
- Iterate: refine the prompt based on output

## Context management
- CLAUDE.md: project conventions and commands Claude should always know
- Skills: reusable instructions loaded when relevant
- Hooks: automatic actions at points in Claude Code's workflow
- MCP: connects AI to tools and data sources
- Less but relevant context beats everything at once

## Verifying output
- AI can be confidently wrong; check facts and APIs
- Run the code and the tests
- Watch for invented functions, packages or config options

## Building AI features
- Tool use: model calls functions you define
- Evals: test set of inputs with expected behaviour; rerun on every change
- Guard against prompt injection from untrusted input
- Limit what tools and permissions the model has

## Lessons from my work
- Good uses so far: generating kubectl/AWS CLI commands, analysing failures, drafting tickets and test steps
- Check generated commands point at the right cluster/account/environment before running
- Strip customer data, keys and credentials before pasting logs or configs into AI tools

## Further reading
- Prompt engineering (Anthropic): https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview
- Building effective agents (Anthropic): https://www.anthropic.com/engineering/building-effective-agents
- Model Context Protocol: https://modelcontextprotocol.io/
- OWASP GenAI security: https://genai.owasp.org/

## Working with coding agents
- Align before coding: agent asks questions and proposes a plan first
- Keep scope tight; log improvements for later instead of fixing them now
- Concise output saves tokens and makes changes easier to review
- Always-on behaviours go in CLAUDE.md; task-specific workflows go in skills
- Read third-party skills before installing; they're instructions the model follows
- Good examples to study: mattpocock/skills (grill-me, caveman, diagnose)