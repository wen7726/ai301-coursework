# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift)

<!-- Where the plan states its scope, boundary, and deviation notes,
and where the diff shows what actually changed. What it means for a
diff to match the plan, for an honest deviation to re-tie a mismatch,
and what silent drift looks like in each direction (more than the
plan, or less with no note). The description's fidelity claims read
against the diff live here too: a description claiming more or less
than the diff delivers is silent drift, not a comms problem. -->
### Where it lives

**Eval mode:** Read the practice package's plan-context block, especially the stated scope, implementation steps, allowed file changes, exclusions, test plan, and any deviation notes. Compare these with the candidate PR's unified diff, changed-file list, and description.

**Live mode:** Read `plan.md`, including its scope, implementation steps, and `## Deviations` section. Compare the plan with the committed branch diff produced by `git diff main...HEAD`. Read `pr_draft.md` to verify that the PR summary and change list accurately describe the implementation.

### What good looks like

Every substantive changed file and code modification is supported by the plan or an explicitly documented deviation. Planned work that was not completed is disclosed accurately, and the PR description does not claim behavior that the diff contradicts.

Silent drift occurs when the diff adds unplanned behavior, omits planned work without disclosure, or claims implementation fidelity that the actual changes do not support.

A clearly disclosed limitation or justified deviation is not automatically a failure.


## Test evidence (harness category: not-tested)

<!-- Where the PR shows its proof: the test-evidence section's
before/after against the plan's test plan and the reproduction's own
steps, and the outcome of the repo's own checks or suite. What
decisive looks like (an observable behavior named, the expected-after
stated, the checks' outcome visible) next to "tests pass". -->

### Where it lives

**Eval mode:** Read the plan-context block's test plan and reproduction steps. Compare them with the candidate PR's test-evidence section, including commands, outputs, before-and-after observations, and reported test results. Read the repo-facts block for required repository checks.

**Live mode:** Read the test plan and reproduction steps in `plan.md` and the Unit 2 reproduction materials. Inspect `test_evidence.md` for actual command output, including before-and-after reproduction evidence.

Check the results of the repository's required commands:

- `make test-unit`
- `make test-integration`
- `make lint`
- `make typecheck`

Also consult `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md` for testing requirements.

### What good looks like

The evidence identifies the behavior being tested, records the commands or reproduction steps, and shows observable results that support the implementation claims.

Before-and-after evidence should demonstrate the original problem and the behavior after the change when applicable.

Repository checks should have recorded outcomes rather than unsupported statements such as "all tests pass."

A failing command does not automatically make the PR unacceptable when the failure is accurately recorded, explained, and consistent with the repository's requirements.

Missing commands, invented output, or unsupported claims of successful testing do not satisfy the evidence requirement.


## Diff quality (harness category: unreviewable)

<!-- Where the change itself lives: the unified diff and the commit
list. What a reviewable change looks like (the fix visible, nothing
unrelated riding along) and the debris tells: debug leftovers, dead
code, commented-out blocks, formatting churn, drive-by edits. -->

### Where it lives

**Eval mode:** Inspect the candidate PR's unified diff, changed-file list, and commit information. Compare each substantive change with the issue and the plan-context block.

**Live mode:** Inspect the committed changes using `git diff main...HEAD` and the changed-file summary using `git diff main...HEAD --stat`. Review the changed files and commits on the working branch.

### What good looks like

The diff contains the intended fix and only the changes necessary to implement it, including any justified deviations.

A reviewer can identify the relevant modifications without separating them from unrelated work.

Watch for:

- Debugging print statements or temporary logging.
- Dead code and unnecessary commented-out blocks.
- Unrelated refactoring or formatting churn.
- Accidental generated files or unrelated file modifications.
- Changes that obscure the issue-specific fix.

A change is not automatically unacceptable because it touches multiple files. Judge whether the changes are relevant and reviewable.

Unrelated edits remain a problem even when they are disclosed.

## Standards and comms (harness category: standards-wall)

<!-- Where the repo states its asks (the repo-facts block's PR
template sections, contributing instructions, and stated policy,
including AI-use disclosure) and where the PR honors them: the
stated sections filled with real content, the disclosure present,
explicit maintainer direction in the thread engaged. What compliant
looks like next to boilerplate or a visibly ignored ask. (Whether
the description's claims match the diff is plan fidelity, above.) -->

### Where it lives

**Eval mode:** Read the repo-facts block for the repository's PR template requirements, contribution instructions, AI-use policy, and explicit maintainer directions. Compare these requirements with the candidate PR's title, description, issue reference, testing section, and reviewer notes.

**Live mode:** Read `.github/PULL_REQUEST_TEMPLATE.md`, `docs/CONTRIBUTING.md`, and relevant instructions in the issue discussion. Compare them with the title and description in `pr_draft.md`. Read `voice-guide.md` for additional writing guidance.

### What good looks like

The PR satisfies the repository's mandatory submission requirements with meaningful, accurate information.

Verify applicable requirements, including:

- A clear summary of the change.
- A reference to the relevant issue, such as `Closes #<issue-number>`.
- An accurate list of substantive changes.
- Testing information and honestly reported results.
- Screenshots or a justified N/A when the template requests them.
- Notes for reviewers, including AI-use disclosure when required.
- Any explicit maintainer instructions relevant to the submission.

Boilerplate, empty mandatory sections, or omitted required disclosures do not satisfy repository standards.

Voice and wording suggestions are advisory and must not independently change the verdict.

Whether the description accurately represents the diff is evaluated under Plan fidelity and Description accuracy, not merely writing style.