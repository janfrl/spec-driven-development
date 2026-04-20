# 06 — Implement

**Goal:** Produce working code with test coverage that reflects the spec's intent, not the implementation's accidents.

**Input:** One task from the plan.

**Output:** Tests + implementation, committed separately, all tests passing, no existing tests modified.

**Exit criterion:** All tests pass. `git diff main -- tests/` on the implementation commit shows zero changes to tests added in the test commit. Constitution rules are not violated.

---

## The loop (one task)

```
1. Draft tests   (AI test-author session)
2. Review tests  (human, adversarial)
3. Commit tests  (failing)
4. Implement     (AI code-author session, fresh context)
5. Run tests
6. Diff check    (did any tests change?)
7. Commit code   (passing)
```

## Step 1 — Draft tests

Open a fresh session. Give it:

- The relevant section of the spec
- The task's acceptance criteria
- The task's test names from `plan.md`
- The constitution (or the rules that apply)

Prompt:

> Draft tests for task [ID]. Use the test names from the plan. Each test asserts a behavior from the spec, not an implementation detail. Do not write the implementation. Do not write tests that check internal method calls, field names, or private state — only observable behavior and contracts. If you're unsure what a test should assert, mark it with a skip and a comment rather than inventing a weak assertion.

## Step 2 — Review tests (this is where the human earns their keep)

Ask yourself, for each test:

- **Does this test assert behavior, or does it mirror the code we haven't written yet?** If it's the latter, it's not really a test — it's a description waiting to pass trivially.
- **What edge case is missing?** Empty input? Null? Boundary values? Concurrent access? Locale/timezone?
- **What's the failure mode?** If this test fails, will the error message tell us what broke?
- **Is the assertion *too specific*?** Tests that check exact error strings break on every refactor. Tests that check error *types* or *codes* survive.

Two prompts that help if you want the AI to help you review:

> "For each test, what's one edge case you didn't cover?"
> "Which of these tests would still pass if I deleted the corresponding implementation and returned a hard-coded value?"

Don't hand-write the tests yourself (unless the AI's draft is hopeless). Review is faster than authorship and catches the same issues.

## Step 3 — Commit tests

Commit with a clear message: `test(T001): add failing tests for [task title]`. The tests should fail — that proves they're testing something real.

## Step 4 — Implement

**Start a fresh session.** This is the discipline that prevents the "agent deletes failing tests to make them pass" failure mode that Kent Beck and others have documented. The implementation session doesn't have the test-authoring context in its head; it only sees the committed tests as a spec.

Give the implementation session:

- The task's acceptance criteria
- The constitution
- The failing tests (already in the repo)
- A strict rule: **do not modify any file under `tests/`** (or your equivalent path)

Prompt:

> Implement task [ID]. The tests in [path] must pass. You may not modify any existing test file. If a test seems wrong, stop and flag it — do not "fix" it. Write the minimum code needed to pass the tests. Follow the constitution in `constitution.md`.

## Step 5 — Run tests

The agent runs them. If any fail: iterate. If any test file was modified: reject the change, restore the tests, and try again with a stronger prompt.

## Step 6 — Diff check (automated guard)

Before accepting the implementation commit, run:

```bash
git diff --stat HEAD~1 -- tests/ test/ __tests__/ spec/
```

If this shows any changes, the implementation session edited tests. Roll back and start step 4 over with a more explicit rule. Consider adding this as a pre-commit hook:

```bash
# .git/hooks/pre-commit (example)
if git diff --cached --name-only | grep -qE '^(tests|test|__tests__|spec)/' && \
   git diff --cached --name-only | grep -qE '^(src|lib)/'; then
    echo "✖ This commit modifies both tests and implementation. Split it."
    exit 1
fi
```

This enforces the test/implementation separation at the git level, not at the human-attention level — which is what the user asked for: document the discipline, don't rely on remembering it.

## Step 7 — Commit implementation

`feat(T001): implement [task title]`. Reference the test commit in the message.

## When the task is bigger than expected

If the implementation session keeps failing or the tests keep revealing missing requirements:

- The task was too big → split it, re-plan
- The spec was underspecified → go back to phase 4 for the affected part
- The tests were wrong → go back to step 1, don't patch

Don't push harder on the agent. Pushing harder produces bad code faster.
