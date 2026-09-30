# Evidence guide: where proof lives in a reproduction package

## Environment

### Where it lives
In an eval package, look at the issue context, repo-facts block, and the Environment section of the reproduction report. In live mode, check the GitHub issue, repository documentation, and the student's draft reproduction report.

### What good looks like
The report includes the tool or project version, operating system, and installation method when relevant. If the environment differs from the issue, the difference is clearly explained.

---

## Steps

### Where it lives
In an eval package, look at the Preparation and Execution sections of the reproduction report. In live mode, review the reproduction steps in the student's draft comment.

### What good looks like
The steps are complete enough that another contributor can reproduce the behavior without guessing missing commands, files, or setup. The steps follow the same workflow described in the issue.

---

## Behavior shown

### Where it lives
In an eval package, compare the issue's reported behavior with the reproduction report's Result, Expected, Actual, terminal output, logs, screenshots, or other artifacts. In live mode, compare the issue description with the evidence included in the student's draft report.

### What good looks like
A successful reproduction shows the same behavior described in the issue. A cannot-reproduce can also be valid when the report clearly says it could not reproduce the issue, shows what actually happened, and identifies relevant differences in environment or trigger conditions. A report fails when it claims successful reproduction but its evidence shows a different or adjacent failure.

---

## Honesty

### Where it lives
In an eval package, compare the report's conclusions with the evidence shown in the reproduction report. In live mode, compare the written claims with the attached evidence.

### What good looks like
The report accurately describes what happened. If the issue cannot be reproduced, the report clearly says so instead of claiming success without supporting evidence.

---

## Comms

### Where it lives
In an eval package, review the claim comment, reproduction report, repo-facts contribution policy, issue or PR templates, and any AI-use policy. In live mode, review the repository's contribution documentation together with the student's draft comments.

### What good looks like
The comments follow the repository's stated contribution requirements. If the repository requires disclosure of AI assistance, the candidate must explicitly name the AI tool used and describe the extent of its assistance. Missing either part is a failure. If the repository has no AI-disclosure requirement, the absence of disclosure does not cause failure.