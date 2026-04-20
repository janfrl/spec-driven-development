# Spec-Driven AI Workflow

A portable, tool-agnostic methodology for building software with AI agents. One methodology, loaded into whichever tool you're using.

## Philosophy

Intent is the source of truth, not code. Before writing code, produce a spec. The spec drives both tests and implementation. Tests exist before implementation exists. Documentation lives with the code and evolves with it.

## Workflow

```
Brainstorm → Concept → Constitution → Spec → Plan → Implement → Review
   ↑_______________________________________________________________|
                      (loop per feature)
```

Each phase has its own file in `workflow/`. Read them in order.

## File layout

```
spec-driven-workflow/
├── SKILL.md            ← Claude skill entry point (frontmatter + routing)
├── README.md           ← you are here
├── workflow/           ← the methodology (source of truth)
├── templates/          ← skeletons to copy into your project
└── adapters/           ← notes for loading into non-Claude tools
```

`workflow/` is the only place the methodology lives. `SKILL.md` and the adapters all point here. If you want to change how the workflow works, edit `workflow/*.md` — nothing else.

## Quick start by tool

### Claude Code

Clone into your skills directory. The whole repo *is* a skill:

```bash
# global (available in all projects)
git clone <this-repo> ~/.claude/skills/spec-driven-workflow

# or per-project
git clone <this-repo> ./.claude/skills/spec-driven-workflow
```

Invoke with: *"Let's start a new project using the spec-driven workflow."* Claude will load `SKILL.md` automatically.

### claude.ai (web / desktop / mobile)

Create a Project, upload the contents of `workflow/` and `templates/` as project files. Paste the contents of `SKILL.md` (without the frontmatter block) into the project's custom instructions.

### Claude Code + Vercel agents (same machine)

Vercel's agent skills expect a different directory. Symlink rather than duplicate:

```bash
# Assuming you've already cloned to ~/.claude/skills/spec-driven-workflow
mkdir -p .agents/skills
ln -s ~/.claude/skills/spec-driven-workflow .agents/skills/spec-driven-workflow
```

Edit in one place, both tools see the update.

### Gemini (web)

Create a Gem. Paste the contents of `SKILL.md` (body only, no frontmatter) as system instructions. Upload `workflow/*.md` and `templates/*.md` as knowledge files. Alternatively, Gemini can import a public GitHub repo directly — point it at this repo.

### ChatGPT / Codex

Create a Custom GPT. Paste `SKILL.md` body as instructions. Upload `workflow/` and `templates/` markdown files as knowledge. For Codex CLI, it reads `AGENTS.md` in the project — use `templates/AGENTS.md` as the starting point.

### Cursor / Windsurf / Aider / other IDE agents

These tools read `AGENTS.md` at the project root. Copy `templates/AGENTS.md` to your new project root and reference this methodology from it.

### Any chat UI (fallback)

Open `workflow/01-brainstorm.md` and paste its contents into the chat to start phase 1. Continue phase by phase. Works everywhere, zero setup.

## Using the workflow on a new project

1. Start a brainstorm session in whatever chat UI you prefer.
2. Work through phases 1–3. Output `concept.md` and `constitution.md`.
3. Create a repo. Copy `templates/AGENTS.md` and your `constitution.md` + `concept.md` into it. Commit.
4. Switch to an IDE agent (Claude Code / Codex / Cursor) for phase 4 onward.
5. Per feature: new branch, spec → plan → TDD implement → review → merge.

## Updating the methodology

Fork this repo. Edit `workflow/` files. Commit. Pull in your projects as needed.

## Why this structure

- **One source of truth** (`workflow/`). No duplicated content.
- **Thin adapters.** Each tool loads the same methodology through its own mechanism.
- **Symlinks over copies** where paths differ but content matches (e.g., Claude skills ↔ Vercel skills).
- **Templates separate from methodology.** You can update the *process* without re-pasting every project's starter files, and vice versa.

## Credits

Draws on: Spec-Driven Development (GitHub Spec Kit), Harper Reed's LLM codegen workflow, Kent Beck's augmented coding / TDD with AI, Anthropic's Claude Code best practices, the AGENTS.md convention.
