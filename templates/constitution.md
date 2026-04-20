# Constitution

> The non-negotiable rules for this project. Every spec, plan, and implementation must respect these. To change a rule, open a PR that amends this file *before* the change that would violate it.

**Version:** 0.1
**Last amended:** [date]

---

## §1 — Tech stack

- Language: [e.g., TypeScript 5.x, strict mode always on]
- Runtime: [e.g., Node 20 LTS]
- Framework: [e.g., Next.js 14, App Router]
- Database: [e.g., PostgreSQL 16]
- Package manager: [e.g., pnpm]

**Rule:** No JavaScript files in `src/`. No framework migrations without a separate decision record.

## §2 — Architecture

- [e.g., CLI-first: every feature must be usable from the CLI before any UI is built]
- [e.g., No business logic in UI components. All logic in `lib/` with a tested interface.]
- [e.g., External I/O goes through adapters with timeouts and retries. No raw `fetch` in feature code.]

## §3 — Testing

- Every public function has a test.
- Tests are written before the implementation they cover.
- Tests assert behavior, not implementation details.
- **Existing tests are not modified during feature work.** If a test seems wrong, open a separate issue.
- Test suite runs in under [N] seconds locally. Slow tests are moved to an integration tier.

## §4 — Dependencies

- No new runtime dependency without review.
- Dev dependencies may be added freely but must be pinned.
- No dependencies without active maintenance (last release > 2 years = rejected by default).

## §5 — Security & privacy

- Never log user input, IDs, or tokens.
- No secrets in code. All via environment variables; example values in `.env.example`.
- All external calls have a timeout. No unbounded waits.

## §6 — Performance

- [e.g., p95 response time < 200ms for user-facing endpoints]
- [e.g., Bundle size < 200KB gzipped for the initial page load]
- Performance budgets are enforced in CI where possible.

## §7 — Documentation

- User-facing changes require doc changes in the same PR.
- `AGENTS.md` is updated when commands, scripts, or conventions change.
- Decisions that will confuse future-you go in `decisions/` as short ADRs.

## §8 — Review & merge

- No self-merges to `main`.
- CI green is required, not optional.
- PR description uses the review checklist from `workflow/07-review.md`.

---

## Amendments

| Date | Change | Rationale |
|------|--------|-----------|
|      |        |           |
