<div align="center">

# 🎛️ Ableton Skills

### Claude Skills for Ableton Live producers
### Workflows for Claude Code, Cursor, Codex, and Gemini CLI

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-12-blue)](skills/)
[![Commands](https://img.shields.io/badge/slash%20commands-4-blueviolet)](commands/)
[![Ableton Live](https://img.shields.io/badge/Ableton%20Live-11%2B-orange)](https://www.ableton.com/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

[Quick install](#quick-install) · [Skills](#the-12-skills) · [Commands](#slash-commands) · [Why](#why-this-exists) · [FAQ](#faq) · [Contributing](CONTRIBUTING.md)

</div>

---

## TL;DR

```bash
# Claude Code
git clone https://github.com/glincker/ableton-skills ~/.claude/skills/ableton

# Cursor
git clone https://github.com/glincker/ableton-skills && cp -r ableton-skills/skills/* .cursor/rules/

# Done. Open your AI assistant. Ask: "Make me a 4-bar lo-fi house loop in C minor"
```

You also need an Ableton MCP server. We recommend [`uisato/ableton-mcp-extended`](https://github.com/uisato/ableton-mcp-extended).

---

## Why this exists

Open-source Ableton MCP servers ([`uisato/ableton-mcp-extended`](https://github.com/uisato/ableton-mcp-extended), [`ahujasid/ableton-mcp`](https://github.com/ahujasid/ableton-mcp)) give your AI agent the plumbing to talk to Live. They don't tell it how to actually be useful to a music producer.

Generic Claude knows music theory but won't:

- High-pass your pads at 100 Hz to clean up mud
- Voice-lead a string ensemble while respecting Vln1's range (G3 to G6)
- Catch kick-bass masking at 80 Hz, the most common cause of "muddy mix"
- Humanize a lo-fi hi-hat with the right velocity curve and swing
- Know that a trap beat at 140 BPM is half-time, not slow

This is the prompt-engineering layer on top of the MCP servers. Skills that make a generic AI assistant act like a co-producer.

### Co-pilot, not generator

We do not compete with Suno, Udio, or AIVA. The user owns the melody, emotion, and structure. We handle the mechanical translation tax: track scaffolding, voice leading, velocity curves, mix diagnostics, MIDI cleanup, articulation choices, DAW navigation.

---

## How we compare

| | `ableton-skills` | Generic Claude | `ahujasid/ableton-mcp` | `uisato/ableton-mcp-extended` |
| --- | :---: | :---: | :---: | :---: |
| MCP server included | no | no | yes | yes |
| Producer-aware skills | yes | no | no | no |
| Music-theory voice leading | yes | partial | no | no |
| Mix diagnostic workflow | yes | no | no | no |
| MIDI humanization | yes | no | no | no |
| Genre-aware drum patterns | yes | partial | no | no |
| Slash commands | yes | no | no | no |
| CLAUDE.md drop-in | yes | no | no | no |
| Multi-platform | 4 | n/a | Claude only | Claude + Cursor |
| Active maintenance | yes | n/a | stale | yes |

---

## Quick install

### Claude Code

```bash
git clone https://github.com/glincker/ableton-skills ~/.claude/skills/ableton
```

Drop `CLAUDE.md` into your Ableton project root for project-scoped context:

```bash
cp ~/.claude/skills/ableton/CLAUDE.md /path/to/your/ableton-project/
```

### Cursor

```bash
git clone https://github.com/glincker/ableton-skills
cp -r ableton-skills/skills/* /path/to/your/project/.cursor/rules/
```

### Codex CLI

```bash
git clone https://github.com/glincker/ableton-skills
echo "Reference: $(pwd)/ableton-skills/CLAUDE.md" >> /path/to/your/project/AGENTS.md
```

### Gemini CLI

Same as Codex but reference from `GEMINI.md`.

### MCP server (required separately)

You also need an Ableton MCP server. Install one of:

- [`uisato/ableton-mcp-extended`](https://github.com/uisato/ableton-mcp-extended) (recommended, actively maintained, 200+ tools, ElevenLabs voice generation)
- [`ahujasid/ableton-mcp`](https://github.com/ahujasid/ableton-mcp) (the original, works but stale)

Follow that repo's install instructions, then restart your AI assistant.

---

## The 12 skills

| # | Skill | What it does |
| --- | --- | --- |
| 1 | [`producer-mode`](skills/producer-mode/SKILL.md) | Sets up tracks, picks instruments, scaffolds arrangements from a brief |
| 2 | [`mixer-doctor`](skills/mixer-doctor/SKILL.md) | Diagnoses muddy/harsh/lifeless mixes, suggests EQ/comp/bus moves |
| 3 | [`midi-cleanup`](skills/midi-cleanup/SKILL.md) | Humanizes velocity, fixes voice leading, quantizes intelligently |
| 4 | [`arrangement-coach`](skills/arrangement-coach/SKILL.md) | Promotes Session loops to Arrangement, builds intro/verse/drop/outro |
| 5 | [`sound-designer`](skills/sound-designer/SKILL.md) | Designs synth patches on Operator/Wavetable/Analog/Drift |
| 6 | [`reference-match`](skills/reference-match/SKILL.md) | Translates "make it sound like X" into actionable production moves |
| 7 | [`mastering-prep`](skills/mastering-prep/SKILL.md) | Pre-master audit: headroom, mono, LUFS, frequency balance |
| 8 | [`chord-pro`](skills/chord-pro/SKILL.md) | Generates progressions with proper voicing across instruments |
| 9 | [`groove-builder`](skills/groove-builder/SKILL.md) | Idiomatic drum patterns by genre with humanization |
| 10 | [`sidechain-setup`](skills/sidechain-setup/SKILL.md) | Sidechain compression routing kick to bass, vocal to bed |
| 11 | [`tempo-coach`](skills/tempo-coach/SKILL.md) | Tempo, time signature, half-time vs full-time, swing guidance |
| 12 | [`vocal-chain`](skills/vocal-chain/SKILL.md) | Vocal processing chains for pop/rap/indie/lo-fi/R&B |

More skills coming weekly, see [Roadmap](#roadmap).

---

## Slash commands

| Command | Purpose |
| --- | --- |
| [`/ableton-init`](commands/ableton-init.md) | Bootstrap a clean project: return tracks, master chain, labeled tracks |
| [`/ableton-export`](commands/ableton-export.md) | Pre-export audit: levels, mono, sample rate, bit depth |
| [`/ableton-snapshot`](commands/ableton-snapshot.md) | Save a markdown snapshot of session state |
| [`/ableton-debug`](commands/ableton-debug.md) | Diagnose connection or behavior issues |

---

## Demo

> *"Make a 4-bar lo-fi house loop in C minor: bass, kick, hat, soft pad. Humanize the hat."*

[demo gif placeholder, will record one of `producer-mode` from prompt to populated session]

The skills tell the AI how to interpret that brief like a producer would: pick the right instruments, set the right tempo, voice the chords properly, write idiomatic patterns, then humanize the velocity curve on the hi-hat with accent preservation.

---

## FAQ

<details>
<summary><b>Do I need to install an MCP server separately?</b></summary>

Yes. This repo ships skills (prompt instructions for the AI). The actual DAW connection is handled by an MCP server. We recommend `uisato/ableton-mcp-extended`. Install that, then drop these skills on top.
</details>

<details>
<summary><b>Will this work with Logic Pro / Reaper / FL Studio?</b></summary>

Right now Ableton Live only. Logic and Reaper adapters are in the roadmap (same skills, different DAW backends). The skill content is mostly DAW-portable; what changes is the MCP tool names.
</details>

<details>
<summary><b>Does this generate full songs?</b></summary>

No. This is a co-pilot, not a generator. The user writes melodies, sets the emotion, decides the structure. We handle voice leading, humanization, mix diagnostics, and DAW navigation. If you want full song generation, use Suno or Udio and import the audio.
</details>

<details>
<summary><b>What if I don't have third-party plugins like Spitfire or Serum?</b></summary>

Every skill defaults to stock Ableton instruments and effects (Operator, Wavetable, Analog, Drift, EQ Eight, Compressor, Glue, Limiter). If a skill mentions a third-party plugin it's optional, with a stock fallback.
</details>

<details>
<summary><b>Will this delete my work?</b></summary>

No. Every skill follows a "read before write, confirm before destructive" pattern. The CLAUDE.md template enforces this. You can also use `/ableton-snapshot` before risky changes to checkpoint your session.
</details>

<details>
<summary><b>Does Claude need internet to use these skills?</b></summary>

Claude itself uses internet (Anthropic's API). The skills are local markdown files. Once Claude has loaded a skill, the actual DAW operations happen through the MCP server, which runs locally and talks to Ableton via socket.
</details>

<details>
<summary><b>Can I use these in commercial productions?</b></summary>

Yes. MIT license, no restrictions on output. The AI is a tool you used; the music you make is yours.
</details>

<details>
<summary><b>What's the difference between this and `awesome-claude-skills` lists?</b></summary>

Awesome lists are curation. We're a focused skill bundle for one domain (music production in Ableton). We test skills against a real MCP server, follow a consistent format, and merge contributor PRs. Awesome lists link to skills; we ship skills.
</details>

<details>
<summary><b>I have a skill idea, how do I contribute?</b></summary>

Open a [skill request issue](.github/ISSUE_TEMPLATE/skill_request.md) or PR directly. PRs that follow the `SKILL.md` format and include a tested workflow get merged within 7 days.
</details>

---

## Roadmap

### Shipping next

- [ ] `live-performance`: Session-view setup for live performance/DJ
- [ ] `genre-pack-cinematic`: orchestral template + idiomatic patterns
- [ ] `genre-pack-lofi`: lo-fi hip-hop pack
- [ ] `genre-pack-edm`: EDM/big-room pack
- [ ] `vst-introspect`: auto-detect installed VSTs and map to skills
- [ ] `automation-coach`: when/how to automate parameters

### Multi-DAW

- [ ] Logic Pro adapter, same skills, different MCP backend
- [ ] Reaper adapter
- [ ] FL Studio adapter

### Tooling

- [ ] One-line installer (`npx ableton-skills install`)
- [ ] VS Code extension for skill authoring
- [ ] Public skill registry / browser

---

## Compatibility

| MCP server | Tested | Notes |
| --- | --- | --- |
| `uisato/ableton-mcp-extended` | yes | Recommended. Most tools mapped. |
| `ahujasid/ableton-mcp` | partial | Works for `producer-mode`, `midi-cleanup`. Limited for advanced skills. |
| `jpoindexter/ableton-mcp` | partial | 200+ tools but less actively maintained. |
| Custom / local fork | unknown | If your fork follows the standard tool naming, skills should work. Open an issue if not. |

| AI assistant | Tested | Skill format |
| --- | --- | --- |
| Claude Code | yes | `~/.claude/skills/` |
| Cursor | yes | `.cursor/rules/` |
| Codex CLI | yes | Reference via `AGENTS.md` |
| Gemini CLI | yes | Reference via `GEMINI.md` |
| Continue.dev | unknown | Untested but should work |
| Aider | unknown | Untested |

---

## Credits

This project is inspired by, and credits, every PR author whose work got closed without merge on the original Ableton MCP repo. We honor the contributors:

- @hidingwill (PR #66, #69-71, the 230+ tools work)
- @marcoloco23 (PR #63, handlers/ split)
- @voxxit (PR #53, Command Pattern refactor)
- @jhurliman (PR #51, comprehensive tool surface)
- @grayplex (PR #77, Foundation Repair)
- @LofiFren (PR #84, clip editing, mixer, scenes)
- @meleyal (PR #83, `get_notes_from_clip`)
- @oottoo (PR #82, Arrangement view)
- @bombsandbottles (PR #87, arrangement clip)
- @FelixLueth (PR #86, #88, typo fix + refactor)
- ...and many more.

The skill workflows draw from public music-theory and production knowledge: Adler's *The Study of Orchestration*, Persichetti, Mike Senior's *Mixing Secrets*, Bobby Owsinski's *The Mixing Engineer's Handbook*, and the collective wisdom of r/ableton, r/wearethemusicmakers, and r/edmproduction.

---

## License

[MIT](LICENSE). Made by [Glincker](https://github.com/glincker). PRs get merged.

---

<div align="center">

[Star us on GitHub](https://github.com/glincker/ableton-skills) if this helps your production workflow.

[Issues](https://github.com/glincker/ableton-skills/issues) · [Discussions](https://github.com/glincker/ableton-skills/discussions)

</div>
