# 00 — Overview

## Principles (apply across all phases)

1. **One phase at a time.** Finish phase N before starting N+1. Trying to plan while still brainstorming produces vague plans.
2. **Artifacts over conversations.** Every phase produces a file that's committed to the repo. Chat history is not a deliverable.
3. **Exit criteria are explicit.** Each phase has a test for "done." No handwaving.
4. **Fresh context between turns when roles differ.** The agent that writes tests is not the same session as the agent that writes implementation. This prevents tests from being rewritten to match buggy code.
5. **Human review is not optional.** The methodology works because of what the human checks, not because of what the AI produces.

## Phase exit criteria (at a glance)

| Phase         | Done when…                                                                                              |
|---------------|---------------------------------------------------------------------------------------------------------|
| Brainstorm    | You can describe the system in 3 paragraphs without uncertainty                                         |
| Concept       | A structured doc exists; all open questions are either resolved or listed explicitly                    |
| Constitution  | Non-negotiable rules are written; every rule is testable or enforceable                                 |
| Spec          | A reviewer unfamiliar with the project can describe the feature back to you                             |
| Plan          | Each task is ≤ 1 day of work, has acceptance criteria, and lists its tests                              |
| Implement     | All tests pass, no tests were modified during implementation, constitution rules are not violated       |
| Review        | PR has a self-review checklist, docs are updated, constitution check is green                           |

## What changes between a new project and a new feature

A **new project** goes through all phases starting at Brainstorm.

A **new feature in an existing project** starts at Spec. The constitution already exists and should be *read* (not re-written). If the feature requires violating a constitution rule, that's a separate conversation — fix the constitution first, then the spec.

## When to loop back

- **Mid-implementation you discover a missing requirement** → don't patch it into code. Update the spec, then the plan, then resume implementation.
- **A test you wrote turns out to be wrong** → mark it, raise it in review, don't silently edit.
- **The agent keeps getting stuck on the same task** → the task is too big or the spec is underspecified. Split it; don't push harder on the agent.

## What this workflow is not

- Not a waterfall. Phases are fast. For a small project all six happen in a day. The point is *sequencing*, not duration.
- Not a substitute for judgment. The agent can produce every artifact; the human still has to read them.
- Not universal. Exploratory prototypes or throwaway spikes don't need this. Use it when the code has to survive past the demo.
