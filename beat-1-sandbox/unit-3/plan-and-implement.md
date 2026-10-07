# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

---

## Posted upstream

**GitHub username**

wen7726

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5906819339

I reproduced the documentation mismatch described in Issue #73 and traced the current provider implementation.

`README.md` and `docs/SETUP.md` instruct users to configure `OPENROUTER_API_KEY`, while `.env.example` documents only the `mock` and `openai` providers and defines `OPENAI_API_KEY`. I also inspected `ingestion/embeddings/provider.py`, where the embedding provider factory currently supports only `mock` and `openai`, and the OpenAI provider requires `OPENAI_API_KEY`.

My plan is to update `README.md` and `docs/SETUP.md` so the setup instructions match the provider configuration currently implemented by the project. This change is limited to the documentation mismatch and does not add OpenRouter support or modify runtime behavior.

To verify the change, I will repeat the reproduction checks from Unit 2 and confirm that the setup documentation no longer references `OPENROUTER_API_KEY`, while `.env.example` continues to document the supported `mock` and `openai` configuration.

---

## Your branch

**Branch**

docs/73-sync-llm-config

**Evidence**

### Before

```bash
grep -n "OPENROUTER_API_KEY" README.md
grep -n "OPENROUTER_API_KEY" docs/SETUP.md
grep -n "OPENROUTER_API_KEY" .env.example
grep -n -A5 -B2 "LLM provider" .env.example
grep -n "OPENAI_API_KEY" README.md docs/SETUP.md .env.example
```

Output:

```text
README.md:24:# Configure environment (add your OPENROUTER_API_KEY to .env)
docs/SETUP.md:47:# Edit .env and set your OPENROUTER_API_KEY (required for AI features)

14-VECTOR_DB_URL=http://localhost:8001
15-
16:# LLM provider
17:# Options: "mock" (default, no API key needed), "openai"
18:LLM_PROVIDER=mock
19:OPENAI_API_KEY=sk-your-key-here
20-
21:# App settings

.env.example:19:OPENAI_API_KEY=sk-your-key-here
```

### After

```bash
grep -n "OPENROUTER_API_KEY" README.md
grep -n "OPENROUTER_API_KEY" docs/SETUP.md
grep -n "OPENROUTER_API_KEY" .env.example
grep -n "OPENAI_API_KEY" README.md docs/SETUP.md .env.example
```

Output:

```text
README.md:26:# Use the default mock provider, or set OPENAI_API_KEY in .env to use the OpenAI provider
docs/SETUP.md:47:# Edit .env and set your OPENAI_API_KEY if using the OpenAI provider.
.env.example:19:OPENAI_API_KEY=sk-your-key-here
```

The searches for `OPENROUTER_API_KEY` in `README.md`, `docs/SETUP.md`, and `.env.example` produced no output after the documentation update, confirming that the setup instructions are now consistent with the current provider configuration.

---

## Eval iterations

**Run history**

- First full evaluation: 19/20 scored items (PASS).
- I revised the diagnosis, executability, and honesty guidance after identifying false rejects on clear-accept packages.
- I re-ran targeted evaluations using `--only` for `pkg-05`, `pkg-14`, `pkg-01`, `pkg-10`, and `pkg-20`.
- The targeted evaluation reached 5/5 agreement.
- Final full evaluation: 19/20 scored items (PASS).

**Package analysis**

I selected `pkg-14`.

My rubric initially graded `pkg-14` as **reject**, while the gold label was **accept**.

The candidate plan presented a diagnosis that matched the reproduced behavior, identified the correct subsystem, and described a concrete method for locating the final implementation point through debugging. My original rubric was too strict because it effectively required the exact root cause and implementation location to already be proven before implementation could begin.

I revised the diagnosis and executability guidance so that a supported working hypothesis may pass when it is consistent with the reproduced behavior and paired with a concrete verification step. I also allowed a plan to pass executability when it clearly identifies the relevant subsystem together with a practical method for locating the final edit site. After these revisions, `pkg-14` matched the gold verdict.

**Check rationale**

> Risks and unknowns are honest | The plan's risks, limitations, assumptions, unknowns, and any uncertainty explicitly raised by the issue, reproduction evidence, or thread. | Pass by default unless the plan hides or falsely resolves a material uncertainty that is visible in the package. The plan does not need to invent risks or unknowns when none are materially unresolved. A concrete limitation, trade-off, inability to test a platform, or statement that no additional risk was identified is sufficient when it does not contradict the available evidence. | required

I revised this check after `pkg-05` was incorrectly rejected even though its plan already acknowledged the practical trade-off of one additional network request every 24 hours. My earlier version implicitly expected every acceptable plan to include an additional unknown or risk, even when the implementation direction had already been established by the issue and discussion. The revised wording instead checks whether the plan hides a material uncertainty rather than requiring uncertainty to exist.

**Trade-offs**

Relaxing the diagnosis, executability, and honesty checks could have accidentally allowed previously correct reject packages to become accepted. To verify that this did not happen, I re-ran `pkg-01`, `pkg-10`, and `pkg-20` as canary packages together with `pkg-05` and `pkg-14`. The targeted evaluation produced 5/5 agreement: the two clear-accept packages changed to the correct accept verdict while the reject canaries remained reject, confirming that the revisions improved recall without weakening the other categories.