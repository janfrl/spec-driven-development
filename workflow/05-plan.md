# 05 — Plan

**Goal:** Break the spec into tasks small enough that each one can be implemented and reviewed as a single, comprehensible unit.

**Input:** Finalized spec.

**Output:** `plan.md` (or `specs/<feature>-plan.md`).

**Exit criterion:** Every task is ≤ 1 day of work (or ≤ 1 hour for a hackathon), has explicit acceptance criteria, and lists the tests that must exist before implementation begins.

---

## Plan structure

See `templates/plan.md`. Each task entry contains:

- **ID** (T001, T002, …) for easy reference in commits
- **Title**
- **Depends on** — other task IDs
- **Spec reference** — which section of the spec this implements
- **Acceptance criteria** — 2–5 bullet points, each testable
- **Tests to write first** — names of test cases (not implementations, just what they verify)
- **Constitution touchpoints** — which rules apply

## Prompt to generate the plan

> Read the spec. Break it into tasks of no more than [1 day / 1 hour] of work. For each task, list acceptance criteria and the test cases that must exist before implementation starts. Do not write code. Do not write the tests themselves — just their names and what they check. Order tasks so each can be completed without waiting on later ones where possible. Flag any dependencies explicitly.

## Right-sizing tasks

A task is too big if:
- It touches more than one layer of the architecture
- Its acceptance criteria run more than 5 bullets
- You can't state in one sentence what "done" looks like
- You'd be uncomfortable reviewing it in a single PR

Split ruthlessly. Small tasks are easier for both humans and AIs to get right.

## Dependencies

Prefer wide over deep: many tasks that can run in parallel beat a long chain of dependent tasks, because parallel tasks let you start multiple agent sessions or teammates.

Use `git worktree` if multiple agents will work in parallel — one worktree per task avoids context collisions.

## Handoff to phase 6

Pick the first task. Switch tools if needed (from chat UI to IDE agent). Begin the TDD loop in phase 6. One task, one branch, one PR.
