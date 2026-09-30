# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

---

## Your identity upstream

**GitHub username**

wen7726

---

## Posted upstream

### Claim comment

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5906819339

Hi! I'd like to work on this issue as my first contribution.

I noticed that the README instructs users to configure `OPENROUTER_API_KEY`, while `.env.example` only includes the `mock` and `openai` provider options and does not mention `OPENROUTER_API_KEY`.

My next step is to reproduce the mismatch in a clean environment and post a short reproduction report with the relevant file contents and environment details before making any changes.
---

### Reproduction comment

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5917822562

### Reproduction Report

#### Environment

- Repository: `pathreview-ai301-fa26-s3`
- Commit: `2f4e82f52efbcfcc57d65b3fa5348672163ca088`
- OS: macOS (Darwin 25.6.0, arm64)
- Shell: zsh

#### Steps

1. Clone the repository and enter the project directory.
2. Open `README.md`.
3. Locate the setup instructions.
4. Observe that the README instructs users to configure `OPENROUTER_API_KEY`.
5. Open `.env.example`.
6. Compare the documented LLM provider configuration with the README.

Commands used:

```bash
grep -n "OPENROUTER_API_KEY" README.md
grep -n "OPENROUTER_API_KEY" .env.example
grep -n -A5 -B2 "LLM provider" .env.example
```

#### Expected

The setup instructions in `README.md` and the variables documented in `.env.example` should describe the same LLM provider configuration and required API keys.

#### Actual

`README.md` instructs users to configure `OPENROUTER_API_KEY`, while `.env.example` only documents the `mock` and `openai` providers and only defines `OPENAI_API_KEY`. No `OPENROUTER_API_KEY` entry exists in `.env.example`.

#### Evidence

```text
$ grep -n "OPENROUTER_API_KEY" README.md
24:# Configure environment (add your OPENROUTER_API_KEY to .env)

$ grep -n "OPENROUTER_API_KEY" .env.example
$ echo $?
1

$ grep -n -A5 -B2 "LLM provider" .env.example
14-VECTOR_DB_URL=http://localhost:8001
15-
16:# LLM provider
17:# Options: "mock" (default, no API key needed), "openai"
18:LLM_PROVIDER=mock
19:OPENAI_API_KEY=sk-your-key-here
20-
21:# App settings
```

The second search finds no match (exit status 1), confirming that `.env.example` does not contain an `OPENROUTER_API_KEY` entry. This matches the documentation mismatch described in Issue #73.

---

## Eval iterations

### Run history

I completed several evaluation runs while refining my rubric.

- Initial full run: **17/20** (below the bar). My behavior check was too strict, causing `pkg-09` and `pkg-10` to fail.
- Re-ran `pkg-09`, `pkg-10`, and `pkg-20` using `--only` after revising the behavior check.
- Added a dedicated required AI disclosure check after discovering the disclosure category failure.
- Re-ran `pkg-20` to verify the disclosure check.
- Used additional `--only` runs (`pkg-05`, `pkg-07`, `pkg-19`, and `pkg-20`) as canary tests after loosening checks.
- Final full run: **agreement: 20/20 scored items (PASS).**

---

### Package analysis

I chose **pkg-20**.

My initial rubric graded `pkg-20` as **accept**, while the gold label was **reject**.

The repository requires contributors to disclose AI-assisted work. My original rubric only checked whether repository contribution guidelines were generally followed, so it did not distinguish repositories that explicitly require AI disclosure.

I revised my rubric by adding a dedicated required AI disclosure check that fails whenever a repository requires disclosure but the candidate does not state both the AI tool used and the extent of its assistance. After adding this check, `pkg-20` matched the gold label.

---

### Check rationale

> Required AI disclosure | Repo-facts contribution policy and AI-use policy, plus the candidate claim comment and repro report. | If the repo-facts block says AI assistance must be disclosed, pass only if the candidate explicitly states both the AI tool used and the extent of its assistance. If either the tool or extent is missing, fail. If the repo has no AI-disclosure requirement, pass. | required |

I added this check after my first full evaluation run. My original rubric grouped all repository contribution requirements into one general check, which failed to identify repositories with explicit AI disclosure requirements. Separating AI disclosure into its own required check allowed my rubric to correctly evaluate those repositories while keeping the general contribution check focused on other repository conventions.

---

### Trade-offs

Making the behavior check less strict allowed honest "cannot reproduce" reports that clearly explained differences from the original issue environment to pass, such as `pkg-09` and `pkg-10`. Because loosening a required check could accidentally change previously correct results, I re-ran canary packages with `--only` before performing another full evaluation. This confirmed that the revised behavior check fixed the intended packages without introducing new incorrect classifications.

---

Related paths: `eval-run.txt` in this directory; the skill files in `tools/repro-check/`.