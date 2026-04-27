---
name: tempo-coach
description: Use when the user is unsure about tempo, time signature, or rhythmic feel choices. Examples - "what tempo should this be?", "should I switch to 3/4?", "is 95 BPM right for lo-fi?", "how do I make this feel less stiff rhythmically?".
---

# Tempo Coach

Help the user pick the right tempo, time signature, and rhythmic feel for what they're making. Mostly conversational; minimal DAW writes.

## Workflow

### 1. Understand the context

What is the user trying to achieve? Pull from:

- Genre (each has tempo conventions)
- Reference track (use its tempo as a starting point)
- Mood (slow = sad/contemplative, fast = energetic)
- Use case (sync to video? for a DJ set? for a film cue?)

### 2. Apply genre tempo conventions

| Genre | Typical tempo range | Notes |
| --- | --- | --- |
| Ambient | 50-70 | Often beatless; tempo for harmony pulse |
| Cinematic underscore | 60-90 | Often rubato; click for sync, not feel |
| Lo-fi hip-hop | 70-90 | Half-time feel often makes it feel slower than it is |
| Boom-bap | 85-95 | The classic 90 BPM is the J Dilla sweet spot |
| Hip-hop modern | 75-115 | Trap is often half-time at 140-160 |
| Indie/folk | 80-120 | Rubato common; click vs feel tradeoff |
| Pop | 95-130 | "100 BPM ballad" or "118 BPM dance pop" |
| Rock | 100-160 | Power ballads slower (60-80) |
| House | 120-128 | 124 is the magic number |
| Tech-house | 124-128 | |
| Techno | 125-135 | |
| Trance | 132-140 | |
| EDM/Big Room | 128 | Locked. Don't deviate. |
| Hardstyle | 150-160 | |
| Drum & Bass | 165-180 | 174 is the genre default |
| Jungle | 160-175 | |
| Footwork | 160 | |

### 3. Time signature guidance

| When to use | Time sig |
| --- | --- |
| Most popular music | 4/4 |
| Waltz, classical 3-feel | 3/4 |
| Compound (jig, gospel triplet feel) | 6/8, 12/8 |
| Odd-meter prog/math | 5/4, 7/8, 11/8 |
| Cinematic flexibility | Switch between 4/4 and 3/4 by section |

If user is unsure: **default to 4/4 unless they explicitly want a 3-feel.**

### 4. Half-time vs full-time feel

A common confusion:
- **Trap at 140 BPM** is half-time at 140 — drums hit on every other beat, but tempo is set to 140
- **DnB at 174 BPM** is full-time — drums on 1-3 (kick) and 2-4 (snare) at 174

When the user says "the drums feel slow but I want it to feel fast":
- They likely want full-time at the original tempo (e.g., trap at 140 with hi-hats moving fast = 140 with 16th-note hats)
- Or vice versa: half-time the drums for a heavier feel

Suggest the swap; don't assume.

### 5. Tempo issues to flag

Ask user to play their loop and check:

- **Drag** — feels slower than the click? Adjust micro-timing or reduce humanization
- **Rush** — feels faster than the click? Same fix, opposite direction
- **Tempo doesn't match the vibe** — if the user's chord progression is romantic but they're at 140 BPM, propose dropping to 90 with a half-time feel

### 6. Click track / metronome

If the user is recording live:
- Subdivision: usually 1/4 notes for slow tempos, 1/8 for fast
- Click sound: use Live's stock click; turn off post-recording
- Pre-roll: 1 bar minimum, 2 for tight performances

### 7. Apply (if needed)

If the user accepts a recommendation:
- `set_tempo` and `set_time_signature` if the MCP supports
- Otherwise: tell them the value to change manually

## Don'ts

- Don't change the tempo without explicit approval — half a project's clips will misalign.
- Don't recommend tempo extremes (40 BPM, 220 BPM) without checking the user actually wants that.
- Don't assume 4/4 if the user's loop is in a 3-feel.

## Common scenarios

**"My beat feels stiff"** → Add humanization (see `midi-cleanup`), or check if you should add swing (8-15% on 16th notes for hip-hop, 0% for EDM).

**"This sounds too slow but I don't want to speed up"** → Half-time the drums (notes on every other beat) at the same BPM, gives a faster feel without changing chord-change rate.

**"Can I change time signature mid-song?"** → Yes, but do it cleanly at section boundaries (intro 4/4 → verse 4/4 → bridge 3/4 → chorus 4/4). Mid-bar changes are advanced and usually unintentional.
