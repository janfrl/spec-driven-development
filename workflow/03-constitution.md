# 03 — Constitution

**Goal:** Write down the non-negotiable rules that every later phase must respect.

**Input:** The concept doc. Your preferences. Any team/org standards.

**Output:** `constitution.md` at the project root.

**Exit criterion:** Every rule in the constitution is (a) testable, (b) checkable in a code review, or (c) configurable as a linter/CI rule. Rules that can't be checked will be ignored.

---

## What belongs in the constitution

- **Tech stack decisions** that shouldn't drift (e.g., "TypeScript strict mode, no JavaScript files")
- **Architectural principles** (e.g., "CLI-first, API follows, UI last")
- **Testing policy** (e.g., "Every public function has a test. Tests written before implementation. Do not modify existing tests during feature work.")
- **Dependencies** (e.g., "No new runtime dependencies without review")
- **Security/privacy floor** (e.g., "Never log user input", "All external calls behind a retry with timeout")
- **Performance floor** (e.g., "p95 latency < 200ms for endpoint X")

## What does NOT belong

- Style preferences best handled by linters (use the linter, not the constitution)
- Detailed architecture diagrams (those go in the spec or concept)
- Things you're unsure about (put those in the spec or flag as open questions)

## Template

See `templates/constitution.md` for a starter.

## How the constitution is used in later phases

- **Spec (phase 4):** every requirement must be compatible with the constitution. If not, amend the constitution *first*.
- **Plan (phase 5):** tasks reference which constitution rules apply (e.g., "adds new dependency — review required per §3").
- **Implement (phase 6):** before committing code, the agent checks the constitution. Violations are flagged.
- **Review (phase 7):** the constitution is the merge gate.

## Amending the constitution

Treat it like a law, not a wish list. To change it mid-project:

1. Propose the change in the feature's branch, not silently in a commit.
2. Note what existing code now violates the new rule.
3. Either fix the violations or grandfather them with a TODO.

Constitutions that change without process stop being real constraints.
