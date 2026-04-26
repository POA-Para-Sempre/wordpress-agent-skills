---
name: review-pr
description: Use when reviewing a pull request or validating a proposed patch for correctness, regression risk, docs drift, issue linkage, milestone hygiene, and release impact. Do not use for initial implementation.
---

Review in this order:

1. Confirm the changed behavior matches the intended scope.
2. Check for correctness and regression risk in the touched code paths.
3. Check whether new or materially changed public APIs gained or updated docstrings.
4. Check whether tests, docs, generated docs, comments, examples, changelog entries, and docstrings drifted.
5. Check whether the PR references the correct issue and uses closing keywords appropriately.
6. Check whether labels and milestones match the work.
7. Classify the release impact as major, minor, patch, or none.
8. Confirm that validation was run for the touched scope, including docs validation when the repo has documentation tooling, or that any missing validation is justified.

Do not consider review complete until:
- code and documentation are coherent
- new public APIs have documentation at the code level
- the PR description reflects whether docs and docstrings were checked before opening the PR
- relevant issues are referenced correctly
- fully resolved issues are marked with closing keywords only when appropriate
- issues and PRs have appropriate labels
- issues and PRs are correlated to the right milestone when one exists
- newly discovered follow-up work is tracked when needed

Report findings first.
If there are no findings, state that explicitly and call out residual risk or missing validation.
