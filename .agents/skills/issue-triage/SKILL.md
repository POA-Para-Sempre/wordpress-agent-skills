---
name: issue-triage
description: Use when starting non-trivial work on a GitHub repository that may require issue reuse, duplicate avoidance, labels, milestones, PR linkage, or new follow-up issues.
---

Apply this workflow:

1. Review relevant open issues before implementation.
2. Recheck the relevant issue list before opening a PR and again before merging.
3. Reuse the best-fitting existing issue when one already covers the work.
4. Avoid duplicate issues unless there is a clear scope split.
5. Ensure every issue and PR gets at least one appropriate label.
6. Map work to the best-fitting milestone when one exists.
7. If implementation reveals a real bug, feature, risk, documentation gap, or follow-up that is not already tracked, create a new issue before concluding.

Feature issue policy:
- Non-trivial feature work must be tracked in GitHub issues before implementation.
- Reuse an existing feature issue when it already describes the planned behavior.
- Create a new feature issue when the work changes behavior, adds workflow or UI, introduces a new operator capability, or materially expands default behavior and no issue already tracks it.
- If a feature spans multiple PRs, reference the same issue from each PR and use a closing keyword only on the final PR that fully ships the feature.
- Before a release, verify that fully shipped feature issues were closed and partially shipped feature issues remain open.

Issue maintenance policy:
- Keep the active tracking issue updated with enough context that another operator can understand the current scope without reconstructing it from chat history alone.
- Refresh the issue body or add a summary comment when scope, constraints, implementation strategy, or deferred follow-ups materially change.
- Before merge, verify that the issue still describes what shipped, what was deferred, and any notable operational context.

Issue-to-branch-and-PR linkage policy:
- Every non-trivial implementation branch must have a governing issue.
- Every non-trivial PR must reference that issue in the PR body.
- When the branch name does not encode the issue identifier directly, add an issue comment or other GitHub-visible note that links the issue to the branch and PR.
- Before merge, verify that the issue, branch, and PR are all cross-referenced strongly enough that the implementation trail is easy to follow.

Major work planning policy:
- Major work must be planned against explicit milestones, not only a branch or issue.
- When work spans multiple features, PRs, or release steps, create milestones before implementation starts.
- Break the work into named milestones with concrete completion criteria.
- Link the relevant issues and PRs to those milestones when the hosting platform supports it.
- Update milestone status as implementation lands and PRs merge.
- Before release, confirm which milestones are complete, which remain open, and which follow-up issues still belong to later milestones.

Pull request policy:
- Recheck relevant issues and milestones before opening or merging a PR.
- Ensure non-trivial feature work is linked to an issue before opening the PR.
- Ensure the issue remains linked from both the PR and the active implementation branch context.
- Use a closing keyword such as `Closes #123` only when the PR fully resolves the issue.
- If the PR only partially addresses an issue, reference it without closing language.
- State inferred issue or milestone intent explicitly in the PR body when the exact label or milestone does not exist.
- Include release-impact context in the PR body when the change affects public behavior or shipping scope.
