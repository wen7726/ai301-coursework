# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

---

## Selected issue

### Issue link

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73

---

### Verdict output

```text
All four rubric checks are required (no preferred checks in the rubric), and all four pass.
Issue #73 - "README and env. example disagree about which LLM API key to set" (open, bug / good first issue / docs / tier-1)
- Active project - pass. Not archived; last push to main 2026-09-16
(6 days ago), five recent commits by Aburke225, well inside 12 months.
- Newcomer-sized scope - pass. One coherent outcome - make README-mo and . env. example agree on OPENROUTER_API_KEY/LLM_PROVIDER. Two named files, docs-only, 1-2h estimate, and a good first issue label applied by a COLLABORATOR. No competing deliverables, no design debate, no failed attempts.
- Unclaimed work - pass. assignees: I], 0 comments, timeline holds only four labeled events, and the repo has zero PRs of any state, so nothing is linked. (The Path Review house rule about classmate claim comments never came into play - there are no comments.)
- Contribution policy - pass. docs/CONTRIBUTING md exists; no AI_POLICY-md/AGENTS.md, and nothing in the guide or PR template mentions AI-assisted work, let alone prohibits it. Silence passes.
Its real conditions are terms to follow: conventional commits, branch docs/73-..., green CI on all five jobs.
Fit note (ranking only, one candidate): a Python repo with a documentation fix in two explicitly named files matches your preference for a clear, well-scoped beginner issue - and since it i docs-only there is no @pytest-mark.xfail marker to hunt down.
"item":
https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
"checks": [
{"name": "Active project", "grade": "pass"
"evidence": "archived=false; last push to main 2026-09-16 (6
days before today), 5 recent commits by Aburke225"},
{"name": "Newcomer-sized scope"
', "grade": "pass"
"evidence": "One outcome - 'Make the two files agree' - across
READMEmd and . env. example; 'good first issue'/'tier-1' labels applied by a COLLABORATOR"},
{"name": "Unclaimed work", "grade": "pass"
"evidence": "assignees: []; 0 comments; timeline contains only
4 'labeled' events; repo has 0 pull requests in any state"}, {"name": "Contribution policy", "grade": "pass"
"evidence": "docs/CONTRIBUTING.md has no AI/tooling
restriction; no AI_POLICY.md or AGENTS.md; PR template requires only green CI and tests"}
"verdict": "accept Jump
```

---

## Eval iterations

### Run history

Run 1: agreement 14/20

Run 2: agreement 17/20

Run 3: agreement 20/20 PASS

---

### Issue analysis

Issue: issue-20

My rubric initially accepted issue-20, while the gold label was reject.
The issue looked active and unclaimed, but after reviewing the issue more carefully I realized it requested adding a completely new toolbar feature rather than fixing a small, beginner-sized issue. I tightened my "Newcomer-sized scope" check so feature requests requiring new functionality would no longer automatically pass. After updating the rubric, issue-20 was correctly rejected.

---

### Check rationale

Quoted check from rubric.md:

> **Newcomer-sized scope** — The issue clearly describes one concrete bug fix, documentation update, or small feature affecting a limited number of files and does not propose broad architectural work, multiple independent deliverables, or major new functionality.

I wrote this check because first-time contributors are much more likely to succeed on issues with a single well-defined objective. Large feature requests or architectural changes usually require much more project knowledge and are less suitable as first contributions.

---

### Trade-offs

This stricter scope check may reject some feature requests that are actually easy to implement. I accepted that trade-off because it better distinguishes beginner-friendly issues from larger design work and improved my overall evaluation accuracy.

---

## Selection rationale

I selected issue #73 because it is a documentation-only issue involving two clearly identified files. It matches my current experience level and can realistically be completed within the available time.

My rubric correctly identified that the repository is active, the issue is unclaimed, the contribution policy allows this type of contribution, and the scope is appropriate for a beginner. I also considered that the issue has a "good first issue" label and a clear expected outcome.

I expect claiming the issue to be straightforward because there are currently no assignees or discussion indicating someone else is actively working on it.
