---
name: arrangement-coach
description: Use when the user has a Session-view loop and wants to promote it to a full Arrangement, build sections (intro/verse/drop/break/outro), or extend a 4-bar idea into a 3-minute track. Examples - "turn this loop into a full song", "build me a 2-minute arrangement from this", "promote session to arrangement".
---

# Arrangement Coach

Promote a Session-view loop into a structured Arrangement, or extend a short idea into a full-length track. The user owns the musical content; you handle structural decisions.

## Workflow

### 1. Read what they have

- `get_session_info` — confirm session vs arrangement state
- `get_track_info` for each track — collect all clips currently in Session view
- Identify the loop length (most likely 4 or 8 bars) and the BPM

### 2. Choose a structural template

Ask the user once: "Which structure?"

| Template | Length | Sections |
| --- | --- | --- |
| **Pop** | ~3 min | Intro 8 → V1 16 → Pre 8 → Chorus 16 → V2 16 → Pre 8 → Chorus 16 → Bridge 8 → Chorus 16 → Outro 8 |
| **EDM** | ~4 min | Intro 16 → Build 16 → Drop 32 → Break 32 → Build 16 → Drop 32 → Outro 16 |
| **Lo-fi** | 2-3 min | Intro 4 → Loop A x4 → Variation x2 → Loop A x2 → Tail 4 |
| **Cinematic** | varies | Stmt → Dev → Climax → Resolution. Use rubato; bar count flexible. |
| **Hip-hop** | 2-3 min | Intro 4 → V1 16 → Hook 8 → V2 16 → Hook 8 → Bridge/V3 16 → Hook 8 → Outro 4 |

### 3. Promote loops to arrangement

For each section in the template:
- Identify which Session clips fit (most loops can serve multiple sections by muting/unmuting tracks)
- Use `create_arrangement_clip` (or equivalent) to drop clips at the right bars on the right tracks
- Mute tracks that shouldn't play in that section (intro = drums + bass only; chorus = everything; bridge = strip back)

### 4. Add transitions

- **Risers** before drops (if EDM/pop) — white noise sweep, snare roll, reverse cymbal
- **Drum fills** at section boundaries — tom roll into the chorus
- **Filter automation** — high-pass sweep into a build, low-pass into a break
- **Reverb tail throw** — send the last hit of a section through the delay/reverb return

### 5. Master fader automation (subtle)

- -1 to -3 dB dip in breakdowns
- Slight push (+0.5 dB) into final chorus
- Don't ride more than 3 dB; let the mix do the work

### 6. Confirm

Before applying, summarize: "I'll build a 2:48 EDM structure: intro 16, build 16, drop 32, break 32, build 16, drop 32, outro 16. Drum fills at every section boundary, filter sweep into builds, master fader -2 dB in break. Apply?"

## Don'ts

- Don't rewrite the user's musical content — only arrange existing clips.
- Don't add sections the user didn't ask for ("I added a key change in the bridge").
- Don't apply heavy automation to the master without explicit ask.
- Don't quantize or modify clip contents — that's `midi-cleanup`'s job.

## Example

> User: "I have a 4-bar lo-fi loop, give me a full 2-minute track"

Steps:
1. Read session — 4 tracks (drums, bass, keys, pad), 4-bar loops on all
2. Apply lo-fi template: 2:00 = ~50 bars at 90 BPM
3. Drop clips: intro 4 (just keys + pad), Loop A x4 = 16 (full mix), Variation x2 = 8 (mute drums, add filter sweep), Loop A x2 = 8, tail 4 (just pad with delay throw)
4. Add: subtle volume rise into the full mix, drum fill at the start of variation, reverb wash on the last bar
5. Report and confirm before writing
