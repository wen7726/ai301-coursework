# Plan for Issue #73

## Diagnosis

My Unit 2 reproduction confirmed a documentation mismatch in the project's LLM configuration.

`README.md` instructs users to configure `OPENROUTER_API_KEY`, while `.env.example` documents only the `mock` and `openai` provider options and defines `OPENAI_API_KEY`.

To determine which documentation reflects the current implementation, I inspected the configuration and embedding provider code.

`core/config.py` defines configuration fields for both OpenAI and OpenRouter, but the embedding provider implementation in `ingestion/embeddings/provider.py` only supports two providers: `mock` and `openai`. The `OpenAIEmbeddingProvider` explicitly requires `OPENAI_API_KEY`, and the provider factory rejects any provider other than `mock` or `openai`.

Based on this evidence, the current setup documentation is inconsistent with the provider implementation exposed by the application.

---

## Scope

### In scope

- Update `README.md` so the setup instructions match the provider implementation.
- Update `docs/SETUP.md` to remove the same inconsistent instruction.
- Keep the setup documentation consistent with `.env.example`.
- Verify that all setup documentation refers to the same supported provider configuration.

### Out of scope

- Adding OpenRouter as a supported provider.
- Changing runtime LLM behavior.
- Removing OpenRouter-related configuration fields from `core/config.py`.
- Refactoring the embedding provider implementation.
- Updating unrelated documentation or environment variables.

---

## Files

### Expected files to change

- `README.md`
- `docs/SETUP.md`

### Files inspected as evidence

- `.env.example`
- `core/config.py`
- `ingestion/embeddings/provider.py`

### Planned branch

```
docs/73-sync-llm-config
```

---

## Implementation approach

1. Update the setup instruction in `README.md` so it no longer tells users to configure `OPENROUTER_API_KEY`.
2. Update the matching instruction in `docs/SETUP.md`.
3. Make the setup documentation describe the provider configuration currently implemented by the project (`mock` and `openai`).
4. Document `OPENAI_API_KEY` when describing the OpenAI provider.
5. Leave `.env.example` unchanged unless another inconsistency is discovered during implementation, since it already matches the current provider implementation.
6. Do not modify runtime provider selection or add OpenRouter support as part of this issue.

---

## Test plan

### Before the fix

My Unit 2 reproduction showed:

```text
$ grep -n "OPENROUTER_API_KEY" README.md
24:# Configure environment (add your OPENROUTER_API_KEY to .env)

$ grep -n "OPENROUTER_API_KEY" .env.example
$ echo $?
1
```

`docs/SETUP.md` also currently contains:

```text
# Edit .env and set your OPENROUTER_API_KEY (required for AI features)
```

---

### After the fix

I will run:

```bash
grep -n "OPENROUTER_API_KEY" README.md

grep -n "OPENROUTER_API_KEY" docs/SETUP.md

grep -n "OPENROUTER_API_KEY" .env.example

grep -n -A5 -B2 "LLM provider" .env.example

grep -n "OPENAI_API_KEY" README.md docs/SETUP.md .env.example
```

Expected results:

```text
$ grep -n "OPENROUTER_API_KEY" README.md
(no output)

$ grep -n "OPENROUTER_API_KEY" docs/SETUP.md
(no output)

$ grep -n "OPENROUTER_API_KEY" .env.example
(no output)
```

The provider block in `.env.example` should remain:

```text
# LLM provider
# Options: "mock" (default, no API key needed), "openai"
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
```

The updated setup documentation should refer to `OPENAI_API_KEY` instead of `OPENROUTER_API_KEY`.

The issue is resolved when `README.md`, `docs/SETUP.md`, and `.env.example` no longer provide conflicting setup instructions.

---

## Risks and unknowns

`core/config.py` still defines OpenRouter-related configuration fields, although the current embedding provider implementation does not expose an `openrouter` provider.

Removing those settings or implementing an OpenRouter provider would change application behavior and is outside the scope of this issue.

This change is intentionally limited to aligning the documentation with the provider implementation that currently exists.

---

## Reproduction evidence

This plan is based on the Unit 2 reproduction.

Observed behavior:

```text
README.md:24:# Configure environment (add your OPENROUTER_API_KEY to .env)
```

while `.env.example` contains:

```text
# LLM provider
# Options: "mock" (default, no API key needed), "openai"
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
```

Searching `.env.example` for `OPENROUTER_API_KEY` returns no matches (exit status 1), reproducing the documentation mismatch described in Issue #73.

---

## Deviations

None yet.

If the implementation differs from this plan during development, I will document the differences here before submitting the pull request.