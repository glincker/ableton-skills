# Changelog

All notable changes to `ableton-skills` are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2026-04-25

### Added

- 12 production-ready skills:
  - `producer-mode` — track scaffolding from a brief
  - `mixer-doctor` — mix diagnostic + corrective EQ/comp moves
  - `midi-cleanup` — humanize, voice leading, intelligent quantize
  - `arrangement-coach` — Session → Arrangement promotion
  - `sound-designer` — synth patch design (Operator/Wavetable/Analog/Drift)
  - `reference-match` — translate artist references to actionable moves
  - `mastering-prep` — pre-master audit checklist
  - `chord-pro` — chord progression generation with proper voicing
  - `groove-builder` — drum patterns by genre
  - `sidechain-setup` — sidechain compression routing
  - `tempo-coach` — tempo/time-sig/feel guidance
  - `vocal-chain` — vocal processing chains
- 4 slash commands:
  - `/ableton-init` — scaffold a clean project structure
  - `/ableton-export` — pre-export audit
  - `/ableton-snapshot` — markdown snapshot of session state
  - `/ableton-debug` — connection/behavior diagnostics
- `CLAUDE.md` drop-in template for Ableton projects
- Multi-platform support: Claude Code, Cursor, Codex CLI, Gemini CLI
- GitHub Actions CI for skill frontmatter validation

[Unreleased]: https://github.com/glincker/ableton-skills/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/glincker/ableton-skills/releases/tag/v0.1.0
