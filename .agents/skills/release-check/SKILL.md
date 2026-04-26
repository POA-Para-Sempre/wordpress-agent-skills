---
name: release-check
description: Use when cutting or correcting a release for a GitHub repository and deciding SemVer impact, release readiness, milestone completeness, and release-gate expectations.
---

Classify the change set using strict Semantic Versioning:
- `MAJOR`: backward-incompatible contract or behavior changes
- `MINOR`: backward-compatible new functionality, new workflows, new operator capabilities, or materially expanded default behavior
- `PATCH`: backward-compatible bug fixes, docs-only changes, packaging-only reissues, or process hardening that does not ship new user-facing or runtime capability

Release discipline requirements:

1. Decide the SemVer bump before creating the tag or official release.
2. Justify the bump level in the PR body or release notes.
3. If the repo defines a release gate command, run it before tagging or correcting a release.
4. If multiple PRs are batched into one release, classify the release by the highest-impact shipped change.
5. Do not use the patch segment as a generic release counter.
6. If a published release used the wrong bump, track the correction in an issue before retagging, superseding, or rebuilding the release line.
7. Confirm that complete feature issues are closed and partial feature issues remain open.
8. Confirm that milestone status is coherent with the intended release.
