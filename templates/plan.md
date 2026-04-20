# Plan — [Feature Name]

**Spec:** [link to spec.md]
**Status:** draft | approved | in-progress | done

---

## Task list

### T001 — [Task title]

- **Depends on:** —
- **Spec reference:** FR-01, FR-02
- **Estimate:** [e.g., 1h]
- **Constitution touchpoints:** §3 (testing), §5 (no logging PII)
- **Acceptance criteria:**
  - [ ] [Observable behavior 1]
  - [ ] [Observable behavior 2]
- **Tests to write first:**
  - `[describes the scenario]`
  - `[describes another scenario, including at least one edge case]`

### T002 — [Task title]

- **Depends on:** T001
- **Spec reference:** FR-03
- **Estimate:**
- **Constitution touchpoints:**
- **Acceptance criteria:**
  - [ ]
  - [ ]
- **Tests to write first:**
  - `[test name]`

---

## Task ordering

[If dependencies allow parallelism, note which tasks can run in parallel worktrees.]

- Parallel group A: T001, T002 (independent)
- Sequential: T003 depends on both A tasks
- Parallel group B: T004, T005

## Risk log

| Task | Risk                                    | Mitigation                       |
|------|------------------------------------------|----------------------------------|
| T003 | [e.g., depends on external API we haven't tested] | POC in phase 2; fallback: stub  |

## Definition of done (for the whole feature)

- [ ] All tasks merged
- [ ] Spec's acceptance criteria all verified
- [ ] Docs updated
- [ ] Constitution still respected
