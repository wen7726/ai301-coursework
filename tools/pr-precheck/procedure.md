# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order
<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

1. Identify the review mode before reading the PR package. In live mode, read scope.md and confirm that the target repository is permitted. In eval mode, use only the supplied practice submission and ignore scope.md.

2. Read rubric.md, references/evidence-guide.md, and this procedure to establish the checks, evidence locations, and verdict rule. If rubric.md or procedure.md contains no usable instructions, refuse to grade and identify the missing component.

3. Read the issue description and available discussion. Record the reported problem, expected behavior, acceptance criteria, and relevant repository requirements.

4. Read plan.md before inspecting the implementation. Record the intended scope, expected changed files, implementation steps, test plan, and any documented Deviations. Reading the plan first prevents the implementation from redefining the original scope.

5. Read the actual implementation. In live mode, inspect the committed branch diff using `git diff main...HEAD`. In eval mode, read the diff supplied in the frozen package. Record all changed files and substantive modifications.

6. Read test_evidence.md or the equivalent practice-package evidence. Record reproduction commands, before-and-after results, unit tests, integration tests, lint results, type-check results, and disclosed failures.

7. Read the proposed PR title and description. Compare its summary, issue reference, change list, testing claims, and reviewer notes with the previously collected evidence.

8. Read the repository's PR template, contribution requirements, and AI-use disclosure policy. In eval mode, use the repository-facts information supplied by the package. In live mode, also read voice-guide.md for communication feedback.

9. Do not assign check grades until the initial evidence collection is complete.

## Evidence gathering
<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

1. For plan fidelity, extract the planned changes, excluded work, and documented deviations from plan.md. Compare them file by file and hunk by hunk with the actual diff. Record additions, omissions, and changes outside the stated scope.

2. For issue alignment, compare the issue's expected behavior with the implementation and PR summary. Record whether the change addresses the reported problem and whether any limitations are disclosed.

3. For observable test evidence, extract the test plan and reproduction steps from plan.md. Match each expected test to actual commands and outputs in test_evidence.md or the evaluation package. Distinguish observed results from unsupported claims.

4. For repository checks, identify the required commands from the PR template and contribution guidelines. In Path Review live mode, look for `make test-unit`, `make test-integration`, `make lint`, and `make typecheck`. Record whether each command was attempted, its observed outcome, and any explanation of failure or missing tests.

5. For diff quality, inspect changed files and hunks for unrelated refactoring, debugging statements, accidental files, commented-out code, and modifications that obstruct review. Record exact file paths and relevant changes.

6. For description accuracy, compare each material claim in the PR title and description with the diff, plan, and test evidence. Record contradictions, unsupported success claims, and honestly disclosed limitations.

7. For repository standards, compare the description against the mandatory sections and disclosures in the PR template, repository-facts block, contribution guidelines, and AI policy. Record missing mandatory requirements, including AI-use disclosure when applicable.

8. For communication clarity, inspect the title and description for understandable language. In live mode, compare them with voice-guide.md. Keep style findings separate from required technical checks.

9. Use references/evidence-guide.md to locate evidence in each mode. If evidence is absent, record that it is missing rather than inventing or assuming a result.

## Check execution
<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Execute every check in rubric.md in the order it appears in the checks table.

2. For each check, identify the specified evidence, apply its pass condition, and assign exactly one grade: `pass`, `fail`, or `unclear`.

3. Assign `pass` only when the available evidence satisfies the stated outcome-based condition.

4. Assign `fail` when evidence demonstrates a violation, contradiction, unsupported success claim, or omitted mandatory requirement.

5. Assign `unclear` when the evidence needed to determine the outcome is unavailable or insufficient. Do not infer success from silence.

6. Apply the honest-outcome rule. An accurately disclosed failed test, incomplete implementation, or limitation is not automatically a failure. Evaluate whether the disclosure is consistent with the actual evidence and the rubric's pass condition.

7. Do not reject a package merely for cosmetic differences, description length, or writing style. Grade substantive outcomes.

8. Once the relevant evidence has been gathered, grade each check from those recorded facts without unnecessarily rereading the entire package. Reopen a source only when a contradiction or ambiguity requires verification.

9. Record a concise evidence statement for every check, including the relevant file, command, observed result, or missing evidence.

10. If a necessary procedure step is unspecified, report the gap rather than inventing a replacement process.

## Verdict assembly
<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->

1. Collect all check grades and their weights from rubric.md.

2. Apply the rubric's verdict rule exactly. Return `accept` only when every required check passes.

3. Return `reject` if any required check is graded `fail` or `unclear`. Preferred checks never change the final verdict.

4. Treat an unclear required check as non-passing because the evidence does not establish that the required condition was met.

5. If multiple required checks fail, identify the first failing required check in rubric order as the primary reason for rejection. Include the other failures in the per-check results.

6. Quote or precisely identify the decisive evidence for the primary failure. If the failure is missing evidence, name the missing source and explain what cannot be verified.

7. For an accepted package, briefly identify the evidence supporting readiness. Report preferred-check improvements separately without changing the verdict.

8. Produce a readable per-check summary and actionable corrections for material failures.

9. End the completed review with the exact fenced JSON schema defined in SKILL.md and CONTRACT.md. Include the PR URL or bundle ID, every check name, its grade, a one-line evidence statement, and the binary verdict.

10. Ensure the JSON is valid and contains no additional text after the closing code fence.
