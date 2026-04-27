---
name: ableton-init
description: Bootstrap a fresh Ableton Live project with our preferred bus structure, return tracks, group templates, and color/labeling conventions. Use at the start of a new project.
---

# /ableton-init

Sets up a clean, production-ready Ableton session structure. Run this once per new project before recording or composing.

## What it creates

### Return tracks (3)

| Return | Device chain | Color | Send level |
| --- | --- | --- | --- |
| **A — Verb** | Reverb (Hall preset, decay 2.5s) | Grey | 0 dB unity |
| **B — Delay** | Ping Pong Delay (1/8 dotted, feedback 35%) | Grey | -6 dB |
| **C — Parallel** | Glue Compressor (4:1, fast attack, auto release) | Grey | -∞ (manual) |

### Master bus chain

- EQ Eight (HPF at 30 Hz to remove sub-rumble)
- Glue Compressor (2:1, slow attack, 1-2 dB GR target — bypass by default, on for mixdown)
- Limiter (-1 dB ceiling — bypass by default, on for export)

### Tempo + time signature

- Default 120 BPM, 4/4 (user can override at invocation: `/ableton-init 95 4/4`)

### Empty track palette (8 tracks, color-coded, unarmed)

| # | Type | Name | Color | Purpose |
| --- | --- | --- | --- | --- |
| 1 | MIDI | Drums | Orange | Drum rack / kit |
| 2 | MIDI | Bass | Yellow | Sub / 808 / bass guitar via Tension |
| 3 | MIDI | Chords | Green | Pad, keys, harmonic bed |
| 4 | MIDI | Lead | Purple | Melody, lead line |
| 5 | Audio | Vocals | Pink | Recording slot |
| 6 | Audio | Sample | Blue | Loops, foley, samples |
| 7 | MIDI | Aux 1 | Light blue | Spare for whatever |
| 8 | MIDI | Aux 2 | Light blue | Spare |

## Workflow

1. Verify session is empty (or close to empty). If not, ask: "Session has N tracks already — proceed and add returns + master chain only, or stop?"
2. Set tempo and time signature.
3. Create return tracks with device chains and presets.
4. Insert master bus chain.
5. Create the 8-track palette. Set colors and names. Don't load instruments — that's the user's choice per project.
6. Send all tracks to Return A at -∞ (no auto-send), let the user dial in per track.
7. Save preferences in a `.ams` file (Ableton template) if user wants this as a default.
8. Report back: "Project initialized at 120 BPM. 8 tracks, 3 return tracks, master chain installed (compressor + limiter bypassed). Ready to compose."

## Customization

User can override at invocation:

- `/ableton-init 95 4/4` — set tempo + time sig
- `/ableton-init lofi` — preset for genre (lo-fi loads softer reverb, no limiter, slower default tempo)
- `/ableton-init cinematic` — adds 16 tracks, organizes by section (strings, brass, woodwinds, perc, choir, FX)
- `/ableton-init minimal` — only returns + master, no track palette

## Don'ts

- Don't activate the master limiter by default. Headroom matters during composition.
- Don't auto-send to reverb. Some genres want bone-dry mixes.
- Don't recommend or load third-party plugins. Stock Ableton only — universal compatibility.
- Don't enable record arm on any track. That's destructive on session start.
