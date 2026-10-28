---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

<!-- State, in your words, the one question this tool answers and what
a PR package is: what artifacts it contains and what they are read
against. CONTRACT.md fixes the question; your frame has to say it so
the tool cannot wander into grading something else. -->

Determine whether a candidate pull request is ready to submit. Review the PR package against the issue, implementation plan, repository standards, and actual code changes. Identify missing evidence, unintended changes, and inconsistencies. Grade readiness, not code style alone.

## Inputs and modes

<!-- Define both modes. Live mode: name every input (your plan.md with
its deviation notes, your branch's diff, your draft PR title and
description, your test evidence, your issue), where each comes from,
and what a house-chain student reads instead. The branch's diff is
everything the branch changes relative to the repo's default branch:
`git diff main...HEAD` (three dots), run from the working copy, is
the command that produces it; name the source that concretely. Eval
mode: state that the bundle is the whole world, nothing is fetched,
and every check runs with the full verdict rule. -->

Operate in one of two modes:

**Live mode:** Review a real working branch. Read the issue URL and its discussion, plan.md including any Deviations, the committed branch diff from `git diff main...HEAD`, pr_draft.md containing the proposed PR title and description, and test_evidence.md containing test commands and outputs. Also read `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md` from the Path Review repository.

For a house-chain submission, use the supplied house issue, reproduction materials, plan, and working branch instead of the student's original Unit 3 materials. Apply the same review requirements.

**Eval mode:** Read the complete frozen practice submission supplied by the evaluation harness. Treat that bundle as the entire evidence source. Do not fetch GitHub issues, inspect external repositories, or invent missing information. Apply every rubric check and the complete verdict rule.


## The scope seam (live mode only)

<!-- Tell the tool when to read scope.md, what to do with the rules it
finds there, what to refuse, and what to do when the scope's repo line
is an unfilled placeholder. State that eval mode ignores scope.md
entirely. CONTRACT.md names the required behavior; your frame has to
instruct it. -->

Before grading a live PR, read scope.md and verify that the target repository is permitted. Refuse to grade a PR targeting an out-of-scope repository. If the Repo line contains an unfilled placeholder, stop and explain that scope.md must be configured.

Ignore scope.md entirely in eval mode.


## The voice seam (live mode only)

<!-- Tell the tool when to read voice-guide.md, which outgoing text it
gates (the PR title and description), how to report a broken rule, and
why it never changes the verdict on its own. State that eval mode
ignores it entirely. -->

Read voice-guide.md before reviewing the PR title and description. Check whether the proposed language follows the guide. Report specific violations with suggested corrections.

Voice-guide violations alone must never change an accept verdict to reject. Report them separately from rubric-based failures.

Ignore voice-guide.md in eval mode.


## Component reads

<!-- Tell the tool how the pieces connect: rubric.md defines the
checks and the verdict rule, references/evidence-guide.md maps where
each evidence family lives, procedure.md is executed as written. Say
what the tool does when the procedure is silent on a step (report the
gap, never improvise around it) and what it does when rubric.md or
procedure.md has no content (the refusal rule, stated as an
instruction). -->

Read rubric.md to identify every check, its evidence requirements, pass conditions, weights, and the final verdict rule.

Read references/evidence-guide.md to locate each evidence type in live and eval submissions.

Execute procedure.md in its specified order: Read order, Evidence gathering, Check execution, and Verdict assembly.

If rubric.md or procedure.md is empty or lacks usable grading instructions, refuse to grade and identify the missing component.

If procedure.md does not specify a necessary step, report the procedural gap. Do not invent an alternative process or silently bypass the missing step.


## Verdict and output

<!-- State the binary verdict space (accept means submit, reject means
hold) and instruct the tool to end its reply with the fenced JSON
block below, valid and last, with nothing after it. The schema is
CONTRACT.md's, verbatim; do not edit it. -->

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

Use only two final verdicts:

- `accept`: The PR is ready to submit under the rubric's verdict rule.
- `reject`: The PR must be held because the rubric's verdict rule is not satisfied.

Report each check with its name, grade, and concise supporting evidence. Explain material failures and actionable corrections.

End every completed review with the exact JSON schema already present in this file. The fenced JSON block must contain valid JSON and must be the final content in the response. Do not add text after it.


## Grading discipline

<!-- Write the standing rules the tool grades under: evidence first,
grade the thing not the polish, the rubric decides, the procedure
decides how, and how unclear grades are treated when the rubric's
verdict rule is silent. CONTRACT.md states each as a guarantee; your
frame has to make them instructions. -->

Grade from observable evidence, not assumptions. Compare the issue, plan, committed diff, PR description, and test outputs before deciding.

Evaluate the actual submission rather than its presentation quality. Do not treat a polished description as proof that implementation or testing is correct.

Use rubric.md as the sole authority for check definitions, weights, and verdict aggregation. Use procedure.md to determine how checks are executed.

Assign `pass` only when evidence satisfies the check, `fail` when evidence demonstrates a violation, and `unclear` when available evidence cannot establish the result.

If the rubric does not define how unclear grades affect the verdict, treat unclear as non-passing for required checks. Never invent evidence to resolve uncertainty.

Do not automatically reject a PR merely because a test fails if the failure is accurately disclosed and the rubric permits it. Distinguish honest limitations from missing or misleading evidence.

Never claim to have executed commands, inspected files, or verified results that were not actually available.