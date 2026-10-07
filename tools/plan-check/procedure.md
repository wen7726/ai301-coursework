# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1. Read the issue description to understand the reported problem and expected behavior.
2. Read the thread highlights and note any maintainer guidance, accepted direction, or known constraints.
3. Read the reproduction evidence and record:
   - the reproduced behavior,
   - the environment,
   - the expected behavior,
   - the actual behavior.
4. Read the candidate plan and identify:
   - diagnosis,
   - scope,
   - files to change,
   - implementation approach,
   - test plan,
   - risks and unknowns.
5. Read the candidate plan comment and compare it with the issue thread and repository conventions before grading communication-related checks.

---


## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

For each evidence family, gather the following information before grading.

### Diagnosis

- Compare the diagnosis against the reproduction evidence.
- Record whether the diagnosis explains the reproduced behavior.
- Note whether it is presented as a confirmed cause or clearly identified as a hypothesis.

### Scope

- Record what the plan says is in scope.
- Record what the plan explicitly excludes.
- Compare the scope with the issue's requested change.

### Executability

- Record the files, directories, or repository areas named.
- Record the implementation approach.
- Record any investigation steps that must happen before editing.

### Test plan

- Compare the proposed tests with the reproduction steps.
- Record the expected observable behavior after the fix.
- Check whether the tests would demonstrate success.

### Honesty

- Record any assumptions, risks, unknowns, or implementation uncertainties.
- Note whether they are acknowledged honestly or presented as established facts.
- Record any stated verification steps.

### Communication

- Compare the draft comment with:
  - the issue discussion,
  - maintainer guidance,
  - repository contribution rules,
  - repository AI policy if applicable.
- Record any promises, deadlines, unsupported claims, or missing required disclosures.

---


## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

## Check execution

1. Grade one check at a time using only the evidence gathered for that check.
2. Do not assume facts that are not stated in the issue, reproduction evidence, or plan.
3. If evidence required for a check is genuinely missing, grade the check as **unclear**.
4. For diagnosis, fail only when the proposed cause or direction contradicts the reproduction evidence or depends on a cause the package rules out. Do not require the root cause to be fully proven before implementation if the plan includes a concrete way to verify it.

5. For executability, pass when the plan either names the exact edit location or names a relevant subsystem plus a concrete investigation step for locating it. Do not require exact function names before work can begin.

6. For honesty, start from pass. Fail only when a material uncertainty visible in the issue, repro evidence, thread, or plan is hidden or presented as resolved without support. Do not require the author to invent risks or unknowns.

7. Grade the communication check after all technical checks have been completed.

---

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1. Apply the verdict rule from the rubric.
2. If every required check passes, return **accept**.
3. If any required check fails, return **reject**.
4. Treat **unclear** as **fail**.
5. Quote the evidence supporting the deciding check in the final explanation.
6. If multiple checks fail, list each failed check together with the evidence that caused the failure.