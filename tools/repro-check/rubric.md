# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment recorded | Repro report environment record, issue context, and repo-facts block. | Pass if the report names the tool or project version and operating system, includes the installation method when relevant, and clearly calls out any meaningful difference from the environment targeted by the issue. | required |
| Steps reproducible | Repro report preparation and execution steps, compared with the issue's trigger conditions. | Pass if a stranger has enough information to recreate the starting state and run the trigger without guessing any behaviorally important detail. Exact copy-paste file contents are not required when the report clearly describes the minimal conditions needed to recreate them. Fail when a required command, input condition, or setup detail needed to reach the reported behavior is missing. | required |
| Behavior accounted for | Issue's reported behavior, repro report's Actual or Result section, and attached output or artifacts. | Pass if either the artifacts show the same behavior described by the issue, or the contributor honestly reports that they could not reproduce it, shows what actually happened, and identifies meaningful differences from the issue's conditions. Fail if the report claims successful reproduction but the artifacts show a different or adjacent failure. | required |
| Evidence shown | Terminal output, logs, screenshots, or other artifacts in the repro report. | Pass if the artifact directly demonstrates the behavior the report claims occurred. A statement without supporting output does not pass. | required |
| Outcome stated honestly | Repro report conclusion and the evidence shown. | Pass if the report says exactly what the evidence supports, including an honest cannot-reproduce result when appropriate. Fail if the report claims more than the artifact demonstrates. | required |
| Claim is specific and non-promissory | Candidate claim comment read against the issue context. | Pass if the claim refers to the issue's specific behavior or component, states a concrete investigation or reproduction step the contributor will take next, and does not promise a fix, deadline, assignment, or exclusive reservation of the issue. Generic praise or enthusiasm does not substitute for issue-specific content. | required |
| Required AI disclosure | Repo-facts contribution policy and AI-use policy, plus the candidate claim comment and repro report. | If and only if the repo-facts block explicitly states that AI assistance must be disclosed for the relevant contribution or comment, pass only when the required disclosure is present. If the policy does not explicitly require disclosure, pass this check even if AI use is mentioned. Do not infer a disclosure requirement from a general AI policy. | required |

## Verdict rule

Accept if every required check passes.
Reject if any required check fails.
Treat unclear as fail.