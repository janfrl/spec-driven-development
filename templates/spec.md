# Spec — [Feature Name]

**Status:** draft | in-review | approved | implemented
**Owner:** [name]
**Related:** [links to concept doc, related specs, issues]

---

## Summary

[2–3 sentences. What is this and why does it exist?]

## Goals

- [What this feature achieves, from the user's perspective]
- [Another goal]

## Non-goals

- [Things this feature explicitly does not do]
- [Scope boundaries that might be mistaken for requirements]

## User stories

**As a** [role], **I want to** [action], **so that** [outcome].

[Repeat for each story. Keep them concrete. "As a user, I want a good UX" is not a story.]

## Functional requirements

| ID    | Requirement                                  | Acceptance criteria                           |
|-------|----------------------------------------------|-----------------------------------------------|
| FR-01 | [What the system must do]                    | [How we verify it — observable, not internal] |
| FR-02 |                                              |                                               |

## Non-functional requirements

- **Performance:** [e.g., response time, throughput, resource limits]
- **Accessibility:** [e.g., WCAG AA, keyboard navigation]
- **Compatibility:** [browsers, OS, versions]
- **Observability:** [what gets logged, metered, traced]

## Data model

[Schemas, tables, API shapes. Be specific. Field names, types, constraints.]

## API surface (if applicable)

[Endpoints, methods, request/response shapes, error codes.]

## Error handling

[Don't say "handle errors gracefully." List them:]

| Condition                  | Behavior                                  | User sees                 |
|----------------------------|-------------------------------------------|---------------------------|
| Network unreachable        | Retry 3x with backoff, then fail          | "Can't connect" + retry   |
| Invalid input              | Reject before mutation                    | Inline validation error   |
| [etc.]                     |                                           |                           |

## UI / UX notes (if applicable)

[Sketches, flows, empty states, loading states, error states. Each state is a requirement.]

## Constitution check

- Rules that apply: [list §s]
- Rules that need amendment: [list or "none"]

## Open questions

- [ ] [Question] — [how we'll resolve it]

> Spec is not ready to exit phase 4 until this list is empty.

## Out of scope for this spec (future work)

- [Things considered and deferred, with a one-line rationale]
