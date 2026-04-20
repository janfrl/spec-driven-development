---
name: spec-driven-development
description: Structured workflow for building apps with AI agents — brainstorm, concept, constitution, spec, plan, TDD implementation, review. Use when the user wants to start a new project or feature with AI assistance, or says things like "let's plan this out", "new project", "new feature", or references spec-driven / SDD workflow.
---

# Spec-Driven AI Workflow

Guide the user through one phase at a time. Do not skip ahead. Each phase has an exit criterion; don't move on until it's met.

## Phases

| # | Phase         | File                          | Output                      |
|---|---------------|-------------------------------|-----------------------------|
| 1 | Brainstorm    | `workflow/01-brainstorm.md`   | Raw notes / transcript      |
| 2 | Concept       | `workflow/02-concept.md`      | `concept.md`                |
| 3 | Constitution  | `workflow/03-constitution.md` | `constitution.md`           |
| 4 | Spec          | `workflow/04-spec.md`         | `spec.md`                   |
| 5 | Plan          | `workflow/05-plan.md`         | `plan.md` (task list)       |
| 6 | Implement     | `workflow/06-implement.md`    | Code + tests + commits      |
| 7 | Review        | `workflow/07-review.md`       | PR with checklist           |

## Routing

- **New project** → start at phase 1 (Brainstorm).
- **New feature in existing project** → start at phase 4 (Spec). Read the project's existing `constitution.md` first.
- **User is stuck mid-phase** → re-read that phase file and apply its exit criterion.
- **User skipped phases** → ask whether they want to backfill or proceed; note the risks.

## Read first

Before applying any phase, read `workflow/00-overview.md` for the exit criteria and principles that apply across phases.

## Templates

When a phase produces a document, copy from `templates/` rather than writing from scratch. Templates encode the structure judges/reviewers expect.
