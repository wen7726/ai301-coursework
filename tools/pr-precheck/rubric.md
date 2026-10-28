# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan fidelity | Compare the changed files and hunks in the diff against plan.md, including its scope, implementation steps, and Deviations section. | Every substantive change is supported by the plan or an explicitly documented deviation. Any omitted planned work is disclosed rather than silently hidden. The description does not falsely claim full plan completion. | required |
| Issue alignment | Compare the issue's requested behavior and acceptance criteria against the plan, diff, and PR description. | The implemented work addresses the stated issue. Any remaining limitations are explicitly disclosed, and the description does not claim behavior that the diff contradicts. | required |
| Observable test evidence | Compare the plan's test plan with test_evidence.md or the practice package's test records. | The evidence contains actual commands and observable results relevant to the changed behavior, including before-and-after reproduction evidence when applicable. Missing or unsuccessful checks are accurately disclosed rather than represented as passing. | required |
| Repository checks | Compare the repository's required test, lint, and type-check commands against the recorded command outputs in the test evidence. | Required checks were attempted and their actual outcomes are reported. An expected failure or honestly explained limitation does not automatically fail this check. Unsupported claims of successful testing fail. | required |
| Reviewable diff | Inspect the changed files and hunks in the diff against the issue's scope and the plan. | The diff is focused on the intended change and contains no unrelated refactors, debugging statements, accidental files, or unnecessary commented-out code that obstruct review. | required |
| Description accuracy | Compare the PR title, summary, change list, and testing claims against the actual diff and test evidence. | Material claims accurately describe the implementation and observed results. Limitations, deviations, and incomplete work are not concealed or contradicted. | required |
| Repository standards | Compare the PR description and repository-facts block against the repository's PR template, contribution requirements, and AI-use policy. | Applicable mandatory sections and disclosures are satisfied, including issue references and AI-use disclosure when required. The submission does not omit a mandatory repository requirement. | required |
| Communication clarity | Inspect the PR title and description, and the voice guide in live mode. | The PR is understandable and gives reviewers a clear explanation of its purpose and impact. Minor wording or style issues do not affect readiness. | preferred |

## Verdict rule
<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Grade every check as `pass`, `fail`, or `unclear`, using the evidence specified in the table.

Return `accept` only when all required checks pass. Return `reject` when any required check fails or is unclear. Preferred checks never change the final verdict.

An unclear required check is non-passing because its outcome cannot be verified from the available evidence.

Apply the honest-outcome rule: a disclosed limitation, failed test, or incomplete implementation is not automatically a failure. Evaluate whether the actual change is accurately represented, whether meaningful evidence is observable, and whether the repository's mandatory requirements are satisfied.

Do not accept fabricated test results, unsupported claims of completed work, silent deviations from the plan, or unrelated changes that make the diff difficult to review.
