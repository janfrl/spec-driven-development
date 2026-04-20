# AGENTS.md

> This file is read by AI coding agents (Claude Code, Codex, Cursor, Aider, Gemini CLI, etc.) before they work on this project. Keep it short, concrete, and current.

## Project

[One-paragraph description: what this project does, who it's for, what stage it's at.]

## Methodology

This project follows the spec-driven workflow: [link to your spec-driven-development repo or location of skill].

- `constitution.md` — non-negotiable rules. Read before proposing any change.
- `specs/` — one file per feature; each has a matching `-plan.md`.
- `docs/` — user-facing documentation; must stay in sync with code.

## Commands

```bash
# install
[your install command]

# dev
[your dev command]

# build
[your build command]

# test (run before finishing any task)
[your test command]

# lint / typecheck
[your lint and typecheck commands]
```

## Test discipline

- Tests are written **before** implementation. See `workflow/06-implement.md`.
- **Do not modify existing test files** during feature implementation. If a test seems wrong, stop and flag it.
- New behavior requires new tests. No exceptions.

## Conventions

- Language / framework: [e.g., TypeScript strict, React 18, Node 20]
- Code style: enforced by [linter name] — run `[lint command]` before committing
- Naming: [e.g., PascalCase for components, camelCase for functions]
- Branches: `[prefix]/[task-id]-[short-description]`
- Commit messages: `[type]([task-id]): [message]` (e.g., `feat(T012): add user login`)

## Constraints the agent cannot infer

[Things that aren't obvious from the code — e.g.:]
- Do not add new runtime dependencies without discussion.
- This project must run offline-first; no network calls from core modules.
- User IDs must never appear in logs.
- [Anything else a new teammate would only learn the hard way.]

## Where to look

- Project overview: `README.md`
- Current spec: `specs/`
- Open tasks: `plan.md` or `specs/<feature>-plan.md`
- What's been decided and why: `decisions/` (ADRs, if you keep them)

## Gotchas

[Non-obvious things that will bite the agent. Examples:]
- The dev server needs `.env.local` populated — see `.env.example`.
- Test database resets between runs; don't rely on seeded data persisting.
- [etc.]
