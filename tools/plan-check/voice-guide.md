# Voice guide: how I talk upstream

## Who I am in threads

I am a first-time open source contributor who is learning how to reproduce bugs and contribute responsibly. I focus on reporting what I observed, supporting my statements with evidence, and following the repository's contribution guidelines. Readers should expect clear, honest, and issue-specific communication from me.

---

## Rules I write by

### Rule: Describe only what I verified

Only state observations that I personally confirmed during reproduction. Do not assume the root cause or claim that the bug is reproduced unless the evidence shows it.

- Wrong: "I confirmed the bug is caused by decoder_hcl.go."
- Right: "I reproduced the behavior shown in the issue. I have not investigated the root cause yet."

---

### Rule: Be specific to the issue

Mention the issue's behavior, files, commands, or versions instead of using generic statements.

- Wrong: "I reproduced the problem."
- Right: "I reproduced the mismatch between README.md and .env.example for the LLM API key configuration."

---

### Rule: Promise investigation, not a fix

A claim comment should explain what I will investigate next, but should never promise a solution or timeline.

- Wrong: "I'll fix this today."
- Right: "I'll reproduce the issue first and report my findings before proposing any changes."

---

### Rule: Let the evidence speak

Support every conclusion with terminal output, logs, screenshots, or other artifacts instead of relying on confidence.

- Wrong: "This definitely happens every time."
- Right: "The attached terminal output shows the same behavior described in the issue."

---

## Things I never post

- I fixed it.
- This should be an easy fix.
- I'll have a PR ready today.
- I reproduced it without showing evidence.
- Generic comments such as "Working on this!" without explaining what I will do.