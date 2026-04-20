# Adapters

How to load this methodology into different tools. The content in `workflow/` and `templates/` is the source of truth — nothing here duplicates it.

---

## Claude Code

The whole `spec-driven-workflow/` directory *is* a skill. Drop it into a skills directory:

```bash
# User-level (all projects)
git clone <repo-url> ~/.claude/skills/spec-driven-workflow

# Project-level
git clone <repo-url> ./.claude/skills/spec-driven-workflow
```

Claude auto-discovers it via `SKILL.md`. Invoke by mentioning the workflow: "Let's start a new project using the spec-driven workflow," or "apply the feature-spec phase."

## claude.ai (web / desktop / mobile)

Two options:

**A) Personal skill** (if your plan includes skills): upload the directory.

**B) Project knowledge**: create a Project. Upload every file in `workflow/` and `templates/` as project files. Paste the body of `SKILL.md` (without the YAML frontmatter block) into the Project's custom instructions field.

## Vercel Agents

Vercel's skill directory differs from Claude's. Rather than duplicating, symlink:

```bash
# Already cloned to ~/.claude/skills/spec-driven-workflow
mkdir -p ~/.agents/skills
ln -s ~/.claude/skills/spec-driven-workflow ~/.agents/skills/spec-driven-workflow
```

Edit in one place, both tools see updates. (If the Vercel path differs on your install, check their current docs — the symlink pattern still applies.)

## Gemini (web — Gems)

Create a Gem. Paste the body of `SKILL.md` as system instructions. Upload every file in `workflow/` and `templates/` as knowledge files.

Alternative: Gemini can import a public GitHub repo as context. Point it at this repo's URL and skip the file upload.

## ChatGPT — Custom GPT

Create a Custom GPT. Paste the body of `SKILL.md` as the instructions. Upload `workflow/*.md` and `templates/*.md` as knowledge files. Don't forget to turn off web browsing if you want deterministic behavior.

## Codex (OpenAI) / Codex CLI

Codex reads `AGENTS.md` at the project root. Copy `templates/AGENTS.md` into your new project and reference this methodology repo from it. For global defaults, put `AGENTS.md` in your home directory (Codex will read it as a fallback).

## Cursor / Windsurf

Cursor reads `.cursorrules` (legacy) and `AGENTS.md` (current). Copy `templates/AGENTS.md` to your project root. For methodology-wide rules that apply across all projects, put them in Cursor's user-level rules.

## Aider

Aider supports conventions via `CONVENTIONS.md` or read on-load. Point it at the `workflow/` directory with `--read` flags:

```bash
aider --read workflow/06-implement.md --read constitution.md
```

## Any chat UI — fallback

Open `workflow/01-brainstorm.md` and paste its "Prompt to kick off" section into the chat. Continue phase by phase by pasting subsequent files. No install, works in any tool that accepts text.

---

## Pattern

Notice what's happening: we have **one** methodology (`workflow/`), loaded through each tool's **native mechanism** (skill, Gem, Custom GPT, AGENTS.md, `.cursorrules`, raw paste). We never duplicate content. Updates to `workflow/*.md` propagate everywhere you've linked or re-imported.

If a new tool emerges tomorrow, adding support is: (1) figure out how it loads context, (2) add a section here, (3) optionally add a symlink.
