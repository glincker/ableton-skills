---
name: chord-pro
description: Use when the user wants to generate, voice, or modify chord progressions. Examples - "give me a sad chord progression in C minor", "voice these chords for piano", "what's a good progression for cinematic music?", "extend this progression with more color tones".
---

# Chord Pro

Generate or refine chord progressions with proper voicing. Music-theory grounded — no random Reddit-tier chord stacks.

## Workflow

### 1. Ask if needed

Required: **key + mode**, **mood/genre**, **target instrument**.
Optional: length (default 4 chords), tempo (for rhythmic feel).

If two are missing, ask in one sentence:
> *"What key and what mood?"*

### 2. Choose progression by genre/mood

| Mood/Genre | Reliable progressions (in C / Cm) |
| --- | --- |
| Sad / cinematic | Cm – Ab – Eb – Bb (i-VI-III-VII), or Cm – Gm/Bb – Ab – Eb |
| Hopeful / pop | C – G – Am – F (I-V-vi-IV), or C – Am – F – G |
| Tension | Cm – F – Cm – G7 (i-iv-i-V), or Cm – Bb – Ab – G |
| Neo-soul / R&B | Cmaj7 – Em7 – Am7 – Dm7 (I7-iii7-vi7-ii7), or use modal interchange |
| Lo-fi / chill | Cmaj7 – Fmaj7 – Bb7 – Eb7 (mixolydian feel), or use ii-V-I in jazz extensions |
| Cinematic build | Cm – Ab – Fm – G (Aeolian + V) |
| EDM uplifting | Am – F – C – G (vi-IV-I-V — the "Axis") |
| Modal/dorian | Cm – F – Gm – Cm (i-IV-v-i in dorian) |

### 3. Voice properly

For each chord, place voices according to instrument:

#### Piano (most common)
- LH: Root + 5th (or root + octave) below middle C
- RH: 3rd + 7th (or 3rd + 5th + 9th for color) above middle C
- No closed-position triads in the same octave as the bass

#### String ensemble
- Cello: root (one octave below middle C)
- Viola: 5th (or 3rd in inversion)
- Vln 2: 3rd or 7th (depending on chord quality)
- Vln 1: highest color tone (9, 11, 13)
- **Respect ranges:** Vln1 G3-G6, Vln2 G3-D6, Vla C3-A5, Cello C2-C5

#### Guitar
- Use idiomatic guitar voicings, not piano-translated chords
- Open chords for folk/indie
- Drop-2 voicings for jazz
- Power chords (root + 5th) for rock

#### Pad / synth
- Spread across 2 octaves
- Can use closed voicing in upper register for warmth
- Avoid the muddy zone (root in same octave as bass synth)

### 4. Add color (optional)

If user wants "more color":
- Add 9ths to major chords (Cmaj9 instead of C)
- Add 11ths to suspended chords
- Use 7ths consistently in jazz/neo-soul
- Add altered tones (b9, #11) on V chords for tension

### 5. Voice leading between chords

When moving from one chord to the next, **move each voice by the smallest interval possible**:

- C → F: keep C (root of C, fifth of F), move E down to F, move G up to A
- Avoid parallel fifths and octaves between outer voices
- Keep common tones static when possible

### 6. Apply

Write the chords to the target track using `add_notes_to_clip`. Each chord gets one full bar by default (override if user specified rhythm).

## Don'ts

- Don't write closed-position triads stacked in MIDI without thought to voice leading.
- Don't ignore instrument range — Vln1 cannot play below G3.
- Don't put all voices in the same octave (results in muddy mid-range).
- Don't use 7-note voicings unless the user has a 7+ voice synth or rich pad — they sound like a fist on a piano.

## Example

> User: "Sad progression in F minor for piano"

Output:
- Progression: Fm – Db – Ab – Eb (i-VI-III-VII)
- Bar 1: LH F2-C3, RH Ab3-C4-Eb4 (Fm)
- Bar 2: LH Db2-Ab2, RH F3-Ab3-Db4 (Db, common tone Ab held)
- Bar 3: LH Ab2-Eb3, RH C4-Eb4-G4 (Ab, ascending top voice)
- Bar 4: LH Eb2-Bb2, RH G3-Bb3-Eb4 (Eb, dominant pull back to Fm)

Apply with `add_notes_to_clip`. Length = 1 bar each, velocity 90 default.
