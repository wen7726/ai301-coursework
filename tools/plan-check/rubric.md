# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis grounded in repro evidence | The plan's diagnosis read against the issue description, thread highlights, and reproduction evidence. | Pass if the diagnosis is compatible with the reproduced behavior and gives a plausible implementation direction. A diagnosis may remain partly unverified and may be written as a working theory if the plan includes a concrete investigation or verification step. Fail only if it contradicts the reproduction evidence or depends on a cause that the available evidence rules out. | required |
| Scope is bounded | The plan's scope statement, files-to-touch section, and the issue's requested outcome. | Pass if the plan describes one coherent change, clearly states what is in scope and out of scope, and avoids unrelated refactoring, feature work, or cleanup. | required |
| Plan targets the relevant cause | The plan's proposed changes read against the diagnosis and reproduction evidence. | Pass if the proposed change addresses the repository area or behavior that the evidence points to rather than only hiding the symptom while leaving the underlying issue unchanged. | required |
| Execution is specific enough | The plan's files, repository areas, implementation approach, and investigation steps. | Pass if the plan gives enough information to start work: either specific files/functions are named, or a relevant subsystem is named together with a concrete method for locating the exact edit site. Exact function names and final implementation details are not required before implementation begins. Fail only if the author would still need to guess both where to start and what action to take. | required |
| Test plan proves an observable result | The plan's test plan read against the Unit 2 reproduction steps and evidence. | Pass if the test re-runs the original reproduction or an equivalent real-code check and states a concrete before/after result that would demonstrate the fix. | required |
| Risks and unknowns are honest | The plan's risks, limitations, assumptions, unknowns, and any uncertainty explicitly raised by the issue, repro evidence, or thread. | Pass by default unless the plan hides or falsely resolves a material uncertainty that is visible in the package. The plan does not need to list a risk or unknown merely to satisfy this check. A stated limitation, trade-off, inability to test a platform, or statement that no additional risk was identified is acceptable when it does not contradict the available evidence. | required |
| Plan comment follows thread and repo conventions | The draft plan comment read against the issue thread, repo-facts block, contribution policy, and Path Review house rules. | Pass if the comment accurately summarizes the proposed plan, reflects relevant maintainer or thread guidance, avoids unsupported promises or deadlines, and follows the repository's stated conventions. | required |

## Verdict rule

Accept only if every required check passes.
Reject if any required check fails.
Treat unclear as fail.
Preferred checks, if any are added later, do not change the verdict.