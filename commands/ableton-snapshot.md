---
name: ableton-snapshot
description: Save a structured snapshot of the current Ableton session state - tracks, devices, key parameters, tempo - to a markdown file. Use as a checkpoint before risky changes or to document a session.
---

# /ableton-snapshot

Read the full session state and write it to a markdown file as a human-readable snapshot. Useful as:
- A checkpoint before applying risky changes
- A handover document for collaborators
- Personal versioning ("snapshot before the bridge rewrite")

## What it captures

- **Project metadata**: name, tempo, time signature, total length
- **Tracks**: name, type (MIDI/Audio/Return/Master), color, volume, panning, mute/solo state
- **Devices**: per-track device chain with key parameter values
- **Clips**: per-track clip names, lengths, note count for MIDI
- **Master chain**: full device list with parameters
- **Sends/returns**: routing matrix

## Output format

Default location: `./snapshots/<timestamp>-<sessionname>.md`

Example output:

```markdown
# Snapshot: my-track v3
**Date:** 2026-04-25 14:32
**Tempo:** 95 BPM
**Time sig:** 4/4

## Tracks (8)

### 1. Drums (MIDI, orange)
- Volume: -2.5 dB
- Pan: 0
- Devices: Drum Rack > Compressor (3:1, 4 dB GR) > EQ Eight (HPF 30Hz)
- Clips: lo-fi-kit-loop (4 bars, 64 notes)

### 2. Bass (MIDI, yellow)
- ...

## Master chain
- Glue Compressor (2:1, slow, 1.5 dB GR, bypass)
- Limiter (-1 dB ceiling, bypass)
```

## Workflow

1. Read all session data.
2. Format as markdown.
3. Write to `snapshots/` directory in the project root.
4. Confirm: "Snapshot saved to ./snapshots/2026-04-25-1432-mytrack.md"

## Don'ts

- Don't dump every parameter — focus on what matters (volume, key device settings, not every micro-knob).
- Don't include large clip note arrays — note count is enough.
- Don't overwrite existing snapshots — always timestamp.
