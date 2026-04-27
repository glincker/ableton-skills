---
name: ableton-export
description: Pre-export checklist before rendering audio. Validates levels, headroom, mono compatibility, and sample rate settings. Use right before bouncing to file.
---

# /ableton-export

Run a pre-export audit and surface anything that would compromise the bounced file.

## What it checks

| Check | Pass criteria |
| --- | --- |
| Master peak | Below -1 dB |
| Master headroom | At least -3 dB before limiter |
| Track-level clipping | No track meter in red |
| Mono compatibility | All elements audible in mono fold |
| DC offset on master | None |
| Sub-30Hz content | Filtered or controlled |
| Project sample rate | Matches export setting (44.1 / 48 / 96 kHz) |
| Bit depth | 24-bit for archival, 16-bit only for distribution |
| Render mode | Real-time off (unless using external hardware) |
| Normalize | OFF |
| Convert to mono | OFF (unless explicitly mono export) |
| Inactive devices | Bypass or remove for performance |

## Workflow

1. Read master bus state, track meters, devices.
2. Run each check, mark ✅ or ❌.
3. Print a summary table.
4. If ❌, propose fixes with specific values.
5. If all ✅, give the green light: "Ready to export. Recommended settings: 24-bit, 48 kHz, render off, no normalize."

## Don'ts

- Don't export on the user's behalf — they may want to choose the file location and name.
- Don't apply mastering chain. This is a check, not a process.
- Don't recommend a specific filename pattern unless asked.
