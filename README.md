# Spec-Driven Development

> A portable workflow skill for AI coding agents.

One methodology, installed via the skills CLI into Claude Code, Cursor, Codex, Gemini, GitHub Copilot, Windsurf, Cline, and a dozen+ other AI coding tools.

## Why

AI coding agents are unpredictable to the extent they have to guess at your intent. Two sessions with the same prompt can produce two very different implementations — one that matches what you wanted, one that compiles but misses the point. The gap is how much the agent had to guess.

Spec-driven development (SDD) reduces the guessing. The *specification* is the source of truth, not the code. Before implementation, you produce a spec; the spec drives tests and implementation; tests exist before code exists; documentation stays in sync as part of every merge. The agent still does the typing — just against a contract rather than a vibe.

## Getting started

**1. Install the skill:**

```bash
npx skills add janfrl/spec-driven-development
```

This installs via the [skills CLI](https://skills.sh) and works for 18+ AI coding tools. For web chat UIs, manual install, or unsupported tools, see [Loading into tools](#loading-into-tools).

**2. Start a session and prompt:**

> Let's start a new project using the spec-driven workflow. Begin with the brainstorm phase.

The skill routes you through each phase, applies the right template, and enforces exit criteria.

## Workflow

```
Once per project:   Brainstorm → Concept → Constitution
Per feature loop:   Spec → Plan → Implement → Review  ↺
```

Each phase has a file in `workflow/` with its prompt, exit criterion, and output. Documentation is updated in every Review — no PR merges with stale docs. Tests are written before implementation, in a separate commit, and the implementation session is not permitted to modify them.

## File layout

```
spec-driven-development/
├── SKILL.md            ← skill entry point (frontmatter + routing)
├── README.md           ← you are here
├── LICENSE             ← MIT
├── workflow/           ← the methodology (source of truth)
└── templates/          ← skeletons to copy into your project
```

`workflow/` is the only place the methodology lives. `SKILL.md` points there. To change how the workflow works, edit `workflow/*.md` — nothing else.

## Loading into tools

### Skills CLI (recommended)

```bash
npx skills add janfrl/spec-driven-development
```

Handles Claude Code, Cursor, Codex, Gemini CLI, GitHub Copilot, Windsurf, Cline, AMP, Goose, Kilo, Droid, Kiro CLI, OpenCode, Roo, Trae, VSCode, and more. Auto-detects your tool and installs to the right path. See [skills.sh](https://skills.sh) for the current list and `npx skills find <query>` to discover other skills.

### Manual install (for editing the methodology locally)

If you want to edit `workflow/*.md` and have changes take effect immediately (no reinstall), clone into the standard agents directory:

```bash
git clone https://github.com/janfrl/spec-driven-development ~/.agents/skills/spec-driven-development
```

Then symlink into your tool's skills path. Example for Claude Code:

```bash
# Global (all projects)
mkdir -p ~/.claude/skills
ln -s ~/.agents/skills/spec-driven-development ~/.claude/skills/spec-driven-development

# Or per-project
mkdir -p ./.claude/skills
ln -s ~/.agents/skills/spec-driven-development ./.claude/skills/spec-driven-development
```

For other tools, adapt the symlink target to that tool's skill directory. Changes to `workflow/*.md` are live in every tool you've linked.

### claude.ai (web / desktop / mobile)

The skills CLI doesn't handle web chat UIs.

**A) Personal skill**: Settings > Capabilities > enable Code execution, then Customize > Skills > upload the directory.

**B) Project knowledge**: create a Project, upload all files in `workflow/` and `templates/` as project files, paste the body of `SKILL.md` (without the YAML frontmatter) into the project's custom instructions.

### Gemini (web — Gems)

Create a Gem. Paste the body of `SKILL.md` as system instructions. Upload all files in `workflow/` and `templates/` as knowledge. Alternatively, Gemini can import a public GitHub repo directly — point it at this repo's URL.

### ChatGPT — Custom GPT

Create a Custom GPT. Paste the body of `SKILL.md` as instructions. Upload `workflow/*.md` and `templates/*.md` as knowledge files.

### Aider

```bash
aider --read workflow/06-implement.md --read constitution.md
```

### Any chat UI — fallback

Paste the "Prompt to kick off" section from `workflow/01-brainstorm.md` into the chat. Continue phase by phase. Zero setup, works everywhere.

### Tool not listed?

First check [skills.sh](https://skills.sh) — the CLI may already support it. Otherwise: find where the tool expects skills or context files, adapt the manual install pattern above, and open a PR to add a section here.

## Using on a new project

1. Start a brainstorm session in whatever chat UI you prefer.
2. Work through phases 1–3. Produce `concept.md` and `constitution.md`.
3. Create a repo. Copy `templates/AGENTS.md` and your `constitution.md` + `concept.md` into it. Commit.
4. Switch to an IDE agent (Claude Code / Codex / Cursor) for phase 4 onward.
5. Per feature: new branch → spec → plan → TDD implement → review → merge. The loop stays in phases 4–7; return to phases 1–3 only for a significant pivot.

Note: `templates/AGENTS.md` is for your *new project* (it tells agents how to work in that repo — build commands, conventions). It's separate from this skill, which is how the methodology gets installed.

## Updating the methodology

If you installed via `npx skills add`, re-run it to pull updates. If you installed manually, `git pull` in `~/.agents/skills/spec-driven-development`. To customize the methodology, fork this repo, edit `workflow/` files, and install your fork instead.

## Contributing

PRs welcome. Edit `workflow/*.md` (the source of truth) and open a PR. Changes to templates or tool-loading instructions also welcome. Keep phase files focused — they should fit on one screen where possible.

## License

MIT. See [`LICENSE`](LICENSE).

## Credits

Draws on:

- [Spec-Driven Development — GitHub Spec Kit](https://github.com/github/spec-kit)
- [Harper Reed — My LLM codegen workflow](https://harper.blog/2025/02/16/my-llm-codegen-workflow-atm/)
- [Kent Beck — Augmented Coding: Beyond the Vibes](https://tidyfirst.substack.com/p/augmented-coding-beyond-the-vibes)
- [Anthropic — Claude Code Best Practices](https://code.claude.com/docs/en/best-practices)
- [skills.sh — the open agent skills ecosystem](https://skills.sh)
- [AGENTS.md convention](https://agents.md/)
