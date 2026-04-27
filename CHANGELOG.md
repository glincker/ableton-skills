# Changelog

All notable changes to `ableton-skills` are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 1.0.0 (2026-04-27)


### Features

* /ableton-init command ([8b22974](https://github.com/glincker/ableton-skills/commit/8b229744fb33c3e96ee83a20ce1154de36115adf))
* arrangement-coach ([d59dc5c](https://github.com/glincker/ableton-skills/commit/d59dc5c543d6fd48f1a26df5152e041230ef493c))
* chord-pro ([116245e](https://github.com/glincker/ableton-skills/commit/116245ed256a4659e8bb396e655a14a18543eac7))
* groove-builder ([43d4669](https://github.com/glincker/ableton-skills/commit/43d466966a922680170f9a0d87f94d2350f96fa8))
* mastering-prep ([d8961b6](https://github.com/glincker/ableton-skills/commit/d8961b6d89a9fd4fa0d3e6659c4cf33688cdb285))
* midi-cleanup skill ([a41c6f2](https://github.com/glincker/ableton-skills/commit/a41c6f27300fb54938a195a8d8db52efa688937b))
* mixer-doctor ([d168ded](https://github.com/glincker/ableton-skills/commit/d168dede2e1f7bc3a7136c90734c27679ff65448))
* more slash commands ([558de02](https://github.com/glincker/ableton-skills/commit/558de026d73d3625bcfc2ca4e817d5518ee312a1))
* producer-mode skill ([1eb168e](https://github.com/glincker/ableton-skills/commit/1eb168e755c11008095003c0d2e43a81fdf94555))
* reference-match ([5d4cee2](https://github.com/glincker/ableton-skills/commit/5d4cee24662b5c71226c050ac4e652f3c85b050a))
* sidechain-setup ([ace5489](https://github.com/glincker/ableton-skills/commit/ace54898275d53b370ce4c1da2e33335143d8fe7))
* sound-designer ([5478646](https://github.com/glincker/ableton-skills/commit/547864630878033729876e8032736b3b8fbbdfbd))
* tempo-coach ([6469c8f](https://github.com/glincker/ableton-skills/commit/6469c8f84e26ed06df5e2aec5304f4a6bee120a9))
* vocal-chain skill ([0960c77](https://github.com/glincker/ableton-skills/commit/0960c775dd777ffb74da217088f4f541103dd0e8))

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
