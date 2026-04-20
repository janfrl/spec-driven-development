# 07 — Review

**Goal:** Ensure the work is mergeable: meets the spec, respects the constitution, is documented, and doesn't regress anything.

**Input:** A branch with one or more completed tasks.

**Output:** A PR with a self-review checklist filled in. Docs updated. CI green.

**Exit criterion:** Every item in the checklist is either checked or explicitly waived with a reason.

---

## Self-review checklist

Copy this into the PR description and fill it in:

```markdown
## Spec alignment
- [ ] Implementation matches every acceptance criterion in the spec
- [ ] Non-goals were not accidentally implemented
- [ ] Error handling covers the cases listed in the spec

## Constitution
- [ ] No constitution rule is violated
- [ ] If a rule was amended, amendment is a separate commit with rationale

## Tests
- [ ] Tests were written before implementation (commit order shows it)
- [ ] No existing tests were modified
- [ ] Test names describe behavior, not implementation
- [ ] All tests pass locally and in CI

## Docs
- [ ] User-facing changes are in the docs
- [ ] Spec is updated if implementation revealed missing requirements
- [ ] AGENTS.md is updated if new commands, scripts, or conventions were added

## Review hygiene
- [ ] PR description explains *why*, not just *what*
- [ ] Commits are atomic and messages are clear
- [ ] No debugging output, no commented-out code, no TODOs without issue links
```

## Using the agent for review

Run a review agent in a fresh session (no context from implementation):

> Review the diff between `main` and this branch. Check: (1) any tests modified, (2) any constitution rules violated, (3) any spec requirements not implemented, (4) any new dependencies not mentioned in the spec. Be adversarial — I want to know what's wrong, not what's good.

A fresh session is less biased toward defending the code it just wrote. This is the writer/reviewer pattern Anthropic recommends for Claude Code.

## Regression check

For anything beyond a trivial change, run the full test suite — not just the feature's tests. The feature tests pass by construction; you need to know nothing else broke.

## Doc update discipline

If the branch changed behavior, the docs must change too. This is how you prevent the drift the user was worried about. The PR doesn't merge until docs reflect reality.

A lightweight rule that works: **if the diff touches a file under `src/`, either a file under `docs/` also changed, or the PR description explains why no doc change was needed.** You can enforce this in CI with a simple check.

## After merge

- Delete the branch.
- If the task revealed a missing requirement, open a ticket or add it to the next iteration's spec. Don't leave it floating in chat history.
- If the workflow itself needed a workaround, note it — the methodology repo should get updated.
