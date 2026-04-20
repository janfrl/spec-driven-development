# 01 — Brainstorm

**Goal:** Go from a vague idea to a shared understanding detailed enough to summarize.

**Input:** A hunch, a problem statement, a few sentences.

**Output:** Notes (conversation transcript or bulleted summary). No formal structure required — that comes in phase 2.

**Exit criterion:** You can describe the system in three paragraphs without saying "I'm not sure about…" Alternately: if an AI restates your idea back to you, you find nothing to correct.

---

## Prompt to kick off (paste into any chat UI)

> I want to brainstorm a new project with you. Ask me one question at a time so we can develop a thorough understanding of the idea. Each question should build on my previous answers. Do not suggest solutions, do not summarize yet, and do not offer multiple questions at once — just one sharp question per turn.
>
> Cover these areas across questions (not in order, and not mechanically — follow the conversation): the problem being solved, the user, the scope and non-scope, the inputs and outputs, the hard constraints (performance, privacy, offline, etc.), the key edge cases, the integrations, and what "done" looks like for the first usable version.
>
> Push back if my answers are vague. Flag contradictions. When you believe the picture is clear enough, ask me "Ready to move to concept?" — and not before.
>
> My idea: [one or two sentences]

---

## Running the phase well

- **Don't let the AI jump to solutions.** If it starts suggesting architectures, redirect: "Not yet — more questions first."
- **Don't let it summarize too early.** A premature summary feels like progress but hides gaps.
- **Answer the actual question.** If you find yourself answering something different, that's a signal the question hit a soft spot in your thinking.
- **Keep it to one chat session.** Context matters here; switching sessions resets the model.

## Handoff to phase 2

When the exit criterion is met, save the transcript (or copy the key points into a scratch file) and move to concept. Don't re-brainstorm in phase 2; concept is about *structuring* what you've already agreed on.
