# Codex Command Rules

This file records the desired command-approval baseline for this repo and for downstream repos bootstrapped from `agentic-standards`.

## Desired always-allow prefixes

- `gh`
- `git`

## Why these prefixes

- `gh` keeps GitHub issue, PR, milestone, and workflow operations available without repeated approval churn.
- `git` keeps normal branch, diff, commit, and merge workflows available without repeated approval churn.

## Important limitation

This file is advisory. It documents the intended execution policy, but it does not itself override Codex sandbox behavior.

The effective always-allow policy still depends on the Codex client or session:

- if the environment supports persistent command-approval rules, mirror `gh` and `git` there
- if the environment does not support repo-driven approval rules, an operator must approve and persist those prefixes manually

## Matching guidance

When possible, prefer plain commands such as `gh pr view` and `git status` so command-prefix matchers can recognize them directly.

Avoid wrapping approved commands in extra shell constructs unless they are actually needed, because some runners stop applying prefix rules once commands are embedded inside more complex shell expressions.
