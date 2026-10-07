# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

### Where it lives

In an eval package, read the issue context, thread highlights, Unit 2 reproduction evidence, and the plan's diagnosis section. In live mode, compare the diagnosis in the student's plan.md with the GitHub issue and the reproduction comment posted in Unit 2.

### What good looks like

The diagnosis is consistent with the reproduced behavior and identifies a plausible cause or affected area supported by the reproduction evidence. A working hypothesis is acceptable when it is clearly identified as a hypothesis and paired with a concrete verification step. It must not contradict the reproduction evidence or present speculation as confirmed fact.

---

## Scope

### Where it lives

Read the plan's scope statement, the files-to-touch section, and the issue description. In live mode, compare the scope in plan.md with the requested behavior in the GitHub issue.

### What good looks like

The plan clearly states what will be changed and what will remain unchanged. The proposed work is limited to solving the reported issue and does not expand into unrelated refactoring, feature work, or cleanup beyond what is needed for the issue.

---

## Executability

### Where it lives

Read the files-to-touch section, implementation approach, work sequence, and any investigation notes in the plan. In live mode, compare the plan with the repository structure.

### What good looks like

The plan identifies the relevant files or repository areas, describes the intended changes, and explains any investigation needed before editing. Another contributor should be able to begin implementation without guessing where to start. Exact function names or final implementation details are not required when the plan provides a concrete way to locate them.

---

## Test plan

### Where it lives

Read the Unit 2 reproduction evidence together with the plan's test plan. In live mode, compare the planned verification steps with the reproduction comment and any commands or expected outputs.

### What good looks like

The test plan re-runs the original reproduction or an equivalent real-code check and states the observable result expected after the fix. Success is demonstrated by measurable behavior rather than a general statement that the issue is fixed.

---

## Honesty

### Where it lives

Read the diagnosis, risks, assumptions, unknowns, and deviations sections of the plan. In live mode, compare the plan with the reproduction evidence, issue thread, and any implementation differences recorded under Deviations.

### What good looks like

The plan does not present a material unresolved question as a confirmed fact and does not ignore an uncertainty explicitly raised by the issue, reproduction evidence, or thread. A plan does not need to invent additional risks or unknowns when none are materially unresolved. A concrete limitation, trade-off, or risk is sufficient evidence of honest planning. If implementation later differs from the original plan, those differences should be recorded under the Deviations section.

---

## Comms

### Where it lives

Read the draft plan comment together with the issue thread, repository contribution policy, repository templates, and AI-use policy if one exists. In live mode, compare the posted plan comment with the GitHub discussion.

### What good looks like

The comment accurately summarizes the planned work, reflects relevant maintainer guidance from the thread, avoids unsupported promises, ownership claims, or deadlines, and follows any repository-specific contribution requirements, including AI disclosure when required.