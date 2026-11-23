# From Issue Discovery to a Merged Pull Request: My First Open-Source Contribution

## Overview

During CodePath AI301, I worked on my first open-source contribution to Ocelot-Social, a social networking project. My goal was to understand how developers contribute to an existing codebase, from finding an issue to submitting a pull request and responding to feedback.

I used AI-assisted tools to help me investigate issues, review documentation, and validate my changes. I eventually contributed a documentation fix that updated an outdated project name in `neo4j/README.md`. My [pull request #10979](https://github.com/Ocelot-Social-Community/Ocelot-Social/pull/10979) was approved and merged on November 18, 2026.

Although the actual code change was small, the process helped me understand why investigating an issue, keeping changes focused, and checking my work are important parts of software engineering.

## What happened

### Finding the right issue

I started by using an Issue Scout tool to search for open-source issues that matched my interests in Python and software engineering.

The initial scan returned 299 unique issues, with 239 remaining after ranking filters. However, I noticed that the results were not as useful as I expected. Several issues came from the same repositories, and the tool accepted an umbrella issue that included multiple independent tasks.

This made me realize that a tool can produce results without necessarily making good decisions.

I revised the Issue Scout rubric to focus more on whether an issue had a clear and manageable scope. I also limited the shortlist to two issues per repository and manually reviewed the candidates instead of relying entirely on the automated results.

After refining my search process, I selected [Ocelot-Social Issue #5331](https://github.com/Ocelot-Social-Community/Ocelot-Social/issues/5331), which involved improving project documentation.

### Investigating the actual problem

Before making changes, I reviewed the issue description and inspected the relevant README files.

One challenge was that the issue had been open for several years. Some of the requested improvements were already present in the repository, including Quick Start instructions and Node version management guidance.

However, I found that `neo4j/README.md` still used the project's previous name, "Human Connection," instead of "ocelot.social."

The original documentation contained:

```text
Human Connection is a social network.
```

The expected wording was:

```text
ocelot.social is a social network.
```

This was my first piece of evidence that a specific documentation inconsistency still existed.

Instead of trying to complete every item from the original issue, I decided to focus on this confirmed problem. I wanted my contribution to be small, relevant, and easy for maintainers to review.

### Implementing and validating the fix

I created a branch named `docs/issue-5331` and updated the opening paragraph of `neo4j/README.md`.

The change was:

```diff
- Human Connection is a social network.
+ ocelot.social is a social network.
```

After editing the file, I used Git commands to inspect the change and check for unintended modifications.

I ran `git show` to review the commit and `git diff --check HEAD^ HEAD` to check for whitespace errors. The diff confirmed that only one file was modified, with one insertion and one deletion. The whitespace check did not report any errors.

Because the change was documentation-only, I did not need to start the Neo4j database to reproduce the original problem. I also checked the pull request's automated validation through GitHub CLI. The initial check summary reported two successful checks, one skipped check, and no failing or pending checks.

I opened [PR #10979](https://github.com/Ocelot-Social-Community/Ocelot-Social/pull/10979), and maintainer Tirokk approved it. The pull request was merged on November 18, 2026.

This was an important result for me because my contribution became part of an existing open-source repository.

### Improving my workflow after the contribution

After the pull request was merged, I continued working on the AI-assisted tools used in the course.

One useful experience came from configuring a Ship Gate to validate my documentation contribution retrospectively.

During the first checks, the PR precheck identified a problem with my draft description. The wording suggested that my change resolved the entire Issue #5331, even though I had only fixed one documentation inconsistency.

I revised the description to use:

```text
Related to #5331
```

I also clarified which issue items were outside the scope of my contribution.

After this revision, the Ship Gate returned PASS, and all eight PR prechecks passed. The documentation build commands, `npm ci` and `npm run docs:build`, also completed successfully.

This validation happened after my PR had already merged, so it was not part of the original approval process. However, it showed me how automated checks can help identify inaccurate descriptions, not just code problems.

I also configured a PR Monitor to track pull request status and generate follow-up drafts. When I ran it against PR #10979, the monitor correctly identified the PR as merged and approved.

It generated a follow-up draft, but I decided not to post it because no further response was necessary. I was also concerned that the suggested wording could imply that the entire issue was ready to close.

This experience reinforced an important lesson: AI-generated suggestions still need human review, especially when communicating with maintainers.

## Limitations and what's next

My contribution was limited to correcting one outdated project name. It did not resolve every documentation improvement listed in Issue #5331, and it did not involve changing application functionality.

Another limitation was that some of my validation tools were configured after the pull request had already merged. Although they helped me evaluate and improve my workflow, I could not use their results as evidence that they influenced the original review.

If I were to make another open-source contribution, I would investigate the current state of the issue more carefully before starting implementation. I would also run my planning and validation tools before opening a pull request rather than afterward.

For future improvements, I would like to make my Issue Scout better at identifying outdated or overly broad issues. I would also improve my PR Monitor so that it checks the actual scope of a contribution before suggesting follow-up messages.

The biggest lesson I learned from this experience is that contributing to open source is not only about writing code. It also requires understanding an existing project, verifying assumptions, communicating clearly, and making changes that other developers can confidently review.
