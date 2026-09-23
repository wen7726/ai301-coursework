# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Active project | Repo-facts block: archived status, last push date, latest release date, and last 5 default-branch commits. | Pass if the repository is not archived and has at least one default-branch commit, branch push, or release within the last 12 months. | required |
| Newcomer-sized scope | Issue body, labels, linked PRs, and comment thread. | Pass unless there is explicit evidence that the work is too broad for a first contribution. Evidence that causes failure includes multiple independent required deliverables, a repository-wide redesign, coordinated changes across multiple repositories, repeated failed implementation attempts or multiple closed implementation PRs indicating substantial unresolved complexity, or a brand-new user-facing capability requiring changes across multiple product surfaces. A task may still pass if it touches multiple files, is technically challenging, or lists multiple possible causes or alternative implementation strategies, as long as they all support one primary requested outcome. Documentation-only tasks with one coherent goal pass. A maintainer- or collaborator-applied `good first issue` or `help wanted` label is positive evidence but is not required. | required |
| Unclaimed work | Repo-facts block: assignees, linked PRs, and issue comment thread. | Pass if the issue has no current assignee, no open linked pull request, and no recent commenter explicitly states they are actively implementing the issue. Closed PRs or abandoned historical claims alone do not count as current ownership. | required |
| Contribution policy | Repo-facts block: contribution policy and any referenced AI/tooling policy. | Pass if the repository either has no relevant contribution policy or explicitly allows assistive AI/tool use while requiring contributors to understand and review their work. Fail only if the policy explicitly prohibits the contribution workflow required by this course. | required |

## Verdict rule

Accept if every required check passes.
Reject if any required check fails.
Treat unclear as fail.