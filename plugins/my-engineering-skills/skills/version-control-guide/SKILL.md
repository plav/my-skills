---
name: version-control-guide
description: Git reference and checklist. Use when committing, branching, merging or rebasing, writing commit messages, resolving conflicts, undoing mistakes in git, or dealing with an accidentally committed secret.
---

# Version control

## Checklist
- Small, focused commits
- Clear commit messages: what and why
- Follow the team's branching strategy
- Pull/rebase often to avoid big conflicts
- Never commit secrets, large binaries or generated files
- Review the diff before committing

## Commit messages
- Short summary line (about 50 chars, imperative: "Add login rate limit")
- Blank line, then body explaining why if needed
- Some teams use Conventional Commits (feat:, fix:, chore:)

## Branching
- Trunk-based: short-lived branches, merge to main often
- Git flow: develop/release branches; heavier process
- Feature branches named after the ticket

## Rebase vs merge
- Merge: keeps full history, adds merge commits
- Rebase: linear history; never rebase shared branches others use
- Squash merge: one commit per PR

## Undoing safely
- Unstage: git restore --staged <file>
- Discard local changes: git restore <file>
- Undo a pushed commit: git revert (safe for shared history)
- Undo local commits: git reset (careful)
- Lost something? git reflog

## Committed a secret?
- Treat it as leaked: rotate it immediately
- Then remove from history if required

## Further reading
- Pro Git book: https://git-scm.com/book/en/v2
- How to write a git commit message: https://cbea.ms/git-commit/
- Conventional Commits: https://www.conventionalcommits.org/
