# AGENTS.md

## Objective
Keep GitHub-centered project work coherent across implementation, documentation, issues, pull requests, milestones, and releases.

## Why this file stays short
- Keep shared root guidance concise and durable.
- Put detailed operational workflows in `.agents/skills/`.
- Put repo-specific commands, paths, and exceptions in repo-local overrides.

## Baseline repository policy
- Keep patches minimal, reversible, and aligned with existing project patterns.
- Run the smallest relevant validation before concluding work.
- Keep user-facing docs, examples, docstrings, and generated documentation aligned with the shipped behavior.
- Add or update detailed documentation for every new or materially changed public surface.
- In Python files, require module docstrings plus detailed docstrings for public functions, classes, and methods.
- In shell scripts and workflow files, require clear top-of-file purpose comments or concise inline comments when the control flow is non-obvious; do not leave non-trivial automation files undocumented.
- Before opening a PR, verify that the proposed diff still matches the relevant docstrings, README content, docs pages, examples, and usage snippets.
- Require each target repo to define its documentation validation path in repo-local overrides.
- When a target repo has documentation tooling, generated docs, or a docs site, run the smallest relevant docs build or docs check as part of PR validation.
- Treat issue, PR, milestone, and release hygiene as part of the implementation.
- Require every issue and pull request to include the three-part issue body structure:
  - `## Summary`
  - `## Requested Outcome`
  - `## Original Request`
- Before concluding an issue, keep the governing PR body synchronized with that issue and ensure the issue side-menu Type is set to one of `Bug`, `Feature`, or `Task`.
- Require all issue and PR automation inputs used by org workflows to be present:
  - Issue type (`Bug`, `Feature`, or `Task`) in the GitHub UI metadata.
  - Repo milestone assignment (use the configured default milestone when one is missing).
  - Org project assignment (at minimum `Org Issue Triage And Dev Automation`).
  - Explicit development linkage to the implementation branch or PR.
  - Assignee set to `diemort` and pull-request reviewer set to `dieBot1` unless temporarily overridden.
  - Open issue Development linkage to an implementation branch when work is active or ready for implementation; use the issue sidebar action `Link a branch, pull request, or create a branch` when the platform UI or API supports it, and keep the linked PR visible there once a PR replaces the standalone branch link.
  - Pull request Development linkage to its governing issue; use a closing keyword such as `Closes #NNN` when the PR fully resolves the issue so GitHub populates `closingIssuesReferences`, and use a non-closing direct reference when the PR only partially addresses the issue.
- Require every issue, including intake, planning, implementation, and follow-up issues, to have native GitHub metadata filled before work concludes:
  - Type selected in the issue side menu: `Bug`, `Feature`, or `Task`.
  - Labels selected, with `bug` mapped to `Bug`, `enhancement` mapped to `Feature`, and otherwise `Task`.
  - Assignee set to `diemort` unless explicitly overridden.
  - Repo milestone selected when milestones are enabled for the repo.
  - Org Project selected, at minimum `Org Issue Triage And Dev Automation`.
  - Development linkage selected in the issue side menu when the issue is active or ready for implementation, using `Link a branch, pull request, or create a branch`.
- Require non-trivial work to start on a branch, not on `main`.
- Require a pull request before merge for non-trivial work; do not push implementation commits directly to `main`.
- Recheck the relevant issue list before implementation, before opening a PR, and before merging.
- Keep the chosen tracking issue current with scope, decisions, constraints, and follow-up context.
- Treat each user request in the prompt as a potential new GitHub issue; if the request is not already tracked and fits issue-level work, create a new issue before implementation proceeds.
- Use the governing issue comments to record the investigation findings, notable decisions, constraints, and root cause or diagnosis as they become clear.
- When any local bot/agent context processes or normalizes an issue, always select a native GitHub Issue Type (`Bug`, `Feature`, `Task`) in the issue side menu and keep it aligned with labels (`bug` -> `Bug`, `enhancement` -> `Feature`, otherwise `Task`).
- Before concluding the work, post the implemented solution summary in the governing issue and link the relevant commit and pull request, or explicitly note when one of those artifacts does not exist.
- Ensure non-trivial work is explicitly linked across issue, branch, and PR, including the GitHub Development section when the platform supports the linkage.
- Treat the platform Codex PR review integration as the default review lane unless a repo explicitly opts into a different review setup.
- For non-trivial PRs, explicitly request Codex review with `@codex review` instead of relying on passive auto-trigger behavior.
- After requesting Codex review, keep monitoring the PR for Codex comments before merging; answer or resolve every Codex comment first, then merge only after Codex gives an explicit OK or approval.
- Keep repo-managed agent automation focused on write-capable implementation flows, not duplicative reviewer workflows.
- When the shared GitHub bot workflow is enabled, route issue edits, comments, branch pushes, pull request creation, merges, and release-related writes through the configured machine-user bot identity instead of `github-actions[bot]`.

## Projects
- Treat GitHub Discussions, Projects, issues, pull requests, milestones, and releases as connected planning and execution lanes, not separate systems.
- Before non-trivial org or repo work, verify overlap in:
  - open or relevant Discussions for prior context
  - the governing Project for active or planned rollout
  - existing implementation issues
- Do not require Discussions as a mandatory starting point.
- If the topic is exploratory, policy-shaping, or architecture-heavy, start it in a Discussion first.
- If the topic is already implementation-ready, start it as an issue/Project item directly.
- If a Discussion drives execution work, carry the Discussion link in the governing issue/PR and keep the Project linkage current.
- Require a governing issue before non-trivial repo migration work or cross-repo standards work begins.
- Require Project linkage for non-trivial cross-repo initiatives, repo migration waves, or org rollout work.
- Require milestone-based planning when work spans multiple repos, multiple pull requests, or multiple rollout phases.
- When one governing issue is expected to span more than one meaningful pull request, branch, or implementation phase, split the work into child issues before continuing implementation.
- Keep the parent issue as the umbrella coordination record, and use child issues for executable slices that can be completed on one branch and one pull request.
- Require every child issue in a multi-PR initiative to carry its own labels, milestone, and Project item; do not leave sub-issues as untracked checklist notes.
- Require one implementation branch per child issue for non-trivial work; branch names should map directly to the child issue, for example `issue-27-project-item-mutations`.
- Require each pull request to close or otherwise directly link one child issue and to reference the parent issue when the work is part of a larger initiative.
- Prefer Project issue items for implementation detail instead of hiding all progress inside one umbrella item; use the parent issue for coordination and child issue items for delivery tracking.
- If implementation on a branch starts to include multiple independent slices, stop and break the remaining work into new child issues and follow-on branches before continuing.
- Require explicit labels on every issue and PR; do not leave issue or PR labels empty.
- Require agents to propose a fitting milestone for non-trivial work, and create or request that milestone when the repo does not already have a suitable one.
- Apply the best-fitting existing milestone when one exists, and do not conclude non-trivial work without resolving the milestone choice.
- Recheck relevant Discussions, Projects, issues, and milestones before implementation, before opening a PR, and before merging.
- If implementation reveals a real gap, follow-up, policy question, or migration blocker that is not already tracked, create a new Discussion (for open questions) or issue (for implementation work) before concluding.
- Record release impact and rollout impact in the governing PR or issue when standards changes affect multiple repositories in the org.

## Data Safety
- Treat queue, state, and artifact metadata DB changes as release-impacting: start from a tracked issue and a rollback plan.
- Require additive schema migrations (`CREATE TABLE`, `CREATE INDEX`, optional `ALTER TABLE ... ADD COLUMN`) and never use destructive migrations in default paths.
- Require explicit backup + restore validation when a PR touches DB schema, queue behavior, or worker persistence logic.
- Require migration smoke checks for:
  - startup with at least one previous schema version,
  - existing rows preserved through migration,
  - crash/retry idempotency of the modified worker path.
- Require a rollback plan and evidence in the PR/issue before merging DB-affecting code.
- Require feature-flagged rollout for new DB-affecting behavior when practical, with staging verification before broad deployment.

## Skills to use
- Use `issue-triage` before non-trivial GitHub work and before opening a PR.
- Use `docs-sync` whenever code, config, CLI, or workflow changes may stale documentation.
- Use `review-pr` when validating a patch or reviewing a pull request.
- Use `release-check` when cutting or correcting a release.
- Use `repo-standards-adoption` when bootstrapping a new repo or installing the shared standard into an existing one.

## Repo-local additions
- Keep each target repo's `AGENTS.md` thin and project-specific.
- Put commands such as tests, lint, docs checks, docs builds, and release gates in repo-local overrides.
- Add directory-level overrides only when a subtree truly follows different rules.
- Keep bot-specific machine-user setup and automation in `fb-post-scraper-bot`, not in the shared org baseline.
