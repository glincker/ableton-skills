# Security Policy

## Reporting a vulnerability

Email security disclosures to **security@glincker.com** with the subject line `[ableton-skills] vulnerability report`.

Do not open public GitHub issues for security problems.

We acknowledge reports within 48 hours and aim to triage within 7 days.

## Scope

This repo ships markdown skill and command definitions. The security boundaries that matter:

- **Skills do not execute code directly.** They are instructions to AI assistants. The assistant decides what to do.
- **MCP server vulnerabilities are out of scope.** Report those upstream to `uisato/ableton-mcp-extended` or `ahujasid/ableton-mcp`.
- **Skill prompt-injection is in scope.** If a skill can be coerced by user input into doing something destructive (e.g., deleting tracks without confirmation), that's a bug.

## What we treat as security issues

- Skills that bypass the "confirm before destructive action" pattern
- Skills that recommend leaking session data or credentials
- Skills that recommend bypassing Ableton's authorization or DAW security
- Skills that disable safety defaults (e.g., master limiter while exporting)

## What is NOT a security issue

- Skill output that produces low-quality music (not a security concern; open a regular issue)
- AI hallucinations about plugin parameters (open an issue tagged `accuracy`)
- MCP server crashes (upstream concern)
