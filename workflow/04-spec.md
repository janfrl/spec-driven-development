# 04 — Spec

**Goal:** Produce a spec detailed enough that a capable developer (human or AI) can implement it without asking follow-up questions.

**Input:** The concept doc (for new projects) or an existing codebase + feature request (for ongoing projects).

**Output:** `spec.md` (for the whole project) or `specs/<feature-name>.md` (for a feature).

**Exit criterion:** A reviewer who hasn't been in the conversation can read the spec and describe back what will be built, including edge cases and error states. If they can't, the spec is not done.

---

## Spec structure

See `templates/spec.md`. The sections are:

1. **Summary** — 2–3 sentences
2. **Goals** — what this feature achieves
3. **Non-goals** — what it explicitly doesn't do
4. **User stories / scenarios** — concrete, testable
5. **Functional requirements** — numbered, each independently verifiable
6. **Non-functional requirements** — performance, accessibility, compatibility
7. **Data model changes** — tables, schemas, APIs
8. **Error handling** — what happens when things go wrong (not an afterthought)
9. **Constitution check** — which rules apply, any amendments needed
10. **Open questions** — if any (should be empty to exit this phase)

## Writing specs with an AI

Paste the relevant parts of the concept doc plus the template, and ask:

> Draft a spec for [feature] using the template structure. Be specific: no "the system should handle errors gracefully" — instead, enumerate which errors and what "handle" means for each. Every functional requirement must have at least one concrete acceptance criterion. If you have to guess at something, mark it "⚠ needs input" rather than filling it in.

Then review. This is the phase where careful review pays off the most — every ambiguity here becomes a bug later.

## The read-back test

Before accepting the spec, hand it to a teammate (or a fresh AI session with no prior context) and ask them to describe what will be built. If their description matches your intent, the spec is done. If not, the spec isn't clear enough yet.

## New feature vs. new project

- **New project:** the spec covers the first usable version. Not v1.0, but the minimum that's worth shipping.
- **New feature:** the spec covers *just this feature*, references existing spec sections it modifies, and calls out integration points.

## Handoff to phase 5

The spec drives the plan. Don't start planning until the spec is stable. Changes to the spec during planning mean you're still specifying — go back to phase 4 before proceeding.
