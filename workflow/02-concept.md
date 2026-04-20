# 02 — Concept

**Goal:** Convert the brainstorm into a structured document. Identify what's settled, what's undecided, and what needs a small proof-of-concept before proceeding.

**Input:** Brainstorm notes / transcript from phase 1.

**Output:** `concept.md` in the project repo (or a shared doc if the repo doesn't exist yet).

**Exit criterion:** The concept doc has no "???" entries. Every open question is either (a) resolved, (b) scoped out, or (c) flagged for a POC with a clear success criterion.

---

## Prompt to produce the concept doc

> Based on our brainstorm, produce a concept document with the following sections:
>
> 1. **Problem** — what are we solving, for whom, and why now
> 2. **Solution at a glance** — 3–5 sentences
> 3. **Scope** — what's in
> 4. **Non-scope** — what's explicitly not in (at least 3 items)
> 5. **Users and use cases** — concrete scenarios
> 6. **Key constraints** — performance, privacy, offline, regulatory, etc.
> 7. **Architecture sketch** — components and how they interact (prose, not code)
> 8. **Open questions** — things we haven't decided, each with a proposed resolution path (research, POC, or "pick one and move on")
> 9. **Risks** — what could go wrong and what we'd do about it
>
> Use my exact phrasing where I was specific. Do not invent details. If something is ambiguous from the brainstorm, mark it "⚠ ambiguous" and move on — don't resolve it silently.

---

## POCs and research

For each open question, decide:

- **Research** (15–60 min): reading docs, checking if a library exists, verifying an API's limits. Do this before moving on.
- **POC** (a few hours): write throwaway code to test a technical assumption. Put it in a `poc/` directory, mark it as throwaway, don't mix it with production code.
- **Decision** (minutes): some questions just need a choice. Make it and document it in the constitution.

Do not proceed to constitution/spec while any open question is unresolved. "We'll figure it out later" is how projects derail.

## Review before proceeding

Read the concept doc out loud (or to someone else). Three tests:

1. Can someone unfamiliar with the project follow it?
2. Do the non-scope items actually protect you from scope creep, or are they too vague?
3. Are any of the "open questions" actually disguised scope decisions you're avoiding?

## Handoff to phase 3

The concept doc is the source material for the constitution (phase 3) and the spec (phase 4). Commit it. Treat it as stable — changes here ripple downstream.
