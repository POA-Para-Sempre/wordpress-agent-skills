---
name: docs-sync
description: Use when a code, config, CLI, or workflow change may have invalidated README content, docs, examples, comments, or docstrings.
---

Apply this workflow:

1. Identify every new or changed public function, class, method, CLI option, config key, API contract, workflow step, and user-visible behavior.
2. Ensure every new or materially changed public symbol has a docstring or equivalent inline API documentation.
3. Check whether each affected docstring or inline usage description still matches the proposed implementation.
4. Check whether `README.md`, `docs/`, examples, comments, changelog entries, generated docs, and usage snippets affected by the change are still correct.
5. Before opening the PR, confirm that the proposed diff, docstrings, and documentation all describe the same behavior.
6. Update documentation immediately when behavior, arguments, return values, side effects, defaults, errors, setup steps, or examples changed.
7. When the repo has documentation tooling, run the smallest relevant docs build or docs validation command before concluding the work.
8. If a document is intentionally not updated, state why it remains correct.

For every modified public symbol or user-facing workflow, verify that the description still matches:
- purpose and scope
- parameters and types
- return value or output shape
- raised errors when applicable
- important side effects
- minimal usage guidance when appropriate

Documentation validation policy:
- Every non-trivial PR must check whether the proposed changes are aligned with docstrings and documentation before the PR is opened.
- Repos that ship generated documentation or a docs site must treat docs build or docs validation as part of normal PR validation.
- Repos that do not generate docs should still validate the repo-local documentation path defined in their overrides.

Never leave missing docstrings for new public APIs, stale docstrings, stale generated docs, stale examples, or stale setup instructions behind after a change.
