# Contributing to ableton-skills

We merge PRs. We do not close them with "fixed."

## Quick rules

- One skill per PR. Don't bundle unrelated changes.
- Skills must be useful to a real producer, not a toy.
- Test your skill against `uisato/ableton-mcp-extended` and document any tools it requires.
- Include at least one example invocation in the SKILL.md.

## Skill format

Every skill is a `SKILL.md` file under `skills/<skill-name>/` with this frontmatter:

```markdown
---
name: skill-name
description: Use when X. Examples - "Y", "Z".
---

# Skill name

Body explaining what it does, the workflow, the don'ts, and at least one example.
```

The `description` field is what the AI uses to decide whether to invoke the skill. Be specific about *when* to use it, with example user phrases.

## Tested platforms

- Claude Code (primary)
- Cursor (skills loaded via `.cursor/rules/`)
- Codex CLI (referenced via `AGENTS.md`)
- Gemini CLI (referenced via `GEMINI.md`)

If your skill only works on one platform, say so in the README.

## Crediting prior work

If your skill builds on a closed/unmerged PR or technique from another repo, credit it in the SKILL.md footer. We honor the work, especially work that got closed without merge elsewhere.

## What we won't merge

- Skills that generate full songs (this is a co-pilot, not Suno).
- Skills that write to the master bus without confirmation.
- Skills that recommend specific paid plugins by default.
- Skills with no example invocation in the SKILL.md.

Otherwise: ship it. We'll review within 7 days.
