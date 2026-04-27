---
name: groove-builder
description: Use when the user wants drum patterns by genre - kick, snare, hi-hat, percussion. Examples - "give me a trap beat", "house drum pattern", "DnB drums at 174", "lo-fi drums with swing", "boom-bap pattern".
---

# Groove Builder

Generate idiomatic drum patterns by genre with proper humanization. Writes to MIDI clips on the user's drum track.

## Workflow

### 1. Identify genre + tempo

Required: genre. Optional: tempo (use genre defaults).

| Genre | Default tempo | Time sig |
| --- | --- | --- |
| Lo-fi hip-hop | 70-90 | 4/4 |
| Boom-bap | 85-95 | 4/4 |
| Trap | 130-150 (half-time feel) | 4/4 |
| House | 120-128 | 4/4 |
| Tech house | 124-128 | 4/4 |
| Techno | 125-135 | 4/4 |
| DnB / Jungle | 165-180 | 4/4 |
| UK garage | 130-138 | 4/4 (shuffled) |
| Drill (UK) | 140-145 (half-time) | 4/4 |
| Reggaeton | 95-100 | 4/4 (dembow) |

### 2. Verify drum rack

`get_track_info` on the drum track. Confirm a drum rack is loaded with at least kick (C1), snare (D1), hat (F#1), and optionally clap (D#1), open hat (A#1), perc (G1+).

If no kit loaded → ask user, or load stock Ableton Drum Kit.

### 3. Write the pattern

For a 1-bar (16-step) pattern, here are tested templates:

#### Lo-fi hip-hop
```
Kick:  X . . . . . X . . . . . . . . .
Snare: . . . . X . . . . . . . X . . .   (snare on 5 & 13 for half-time feel)
Hat:   X . X . X . X . X . X . X . X .   (8th notes)
```
- Kick: vel 100-110
- Snare: vel 90-100, slight late timing (+5ms)
- Hat: vel 65-85, ±15 humanize, swing 8-12%

#### Boom-bap
```
Kick:  X . . X . . X . . . X . . . . .
Snare: . . . . X . . . . . . . X . . .
Hat:   X X X X X X X X X X X X X X X X   (16ths)
```
- Hat: vel 50-80, more aggressive humanize ±20

#### Trap
```
Kick:  X . . . . . . X . . . . . . . .   (sparse, half-time feel)
Snare: . . . . X . . . . . . . X . . .
Hat:   X X . X X X . X X . X X X . X X   (rolling, with stutters)
808:   long held bass notes underneath
```
- Hi-hat rolls: alternate 16ths with 32nd-note bursts
- Open hat occasionally on the off-beat

#### House
```
Kick:  X . . . X . . . X . . . X . . .   (4-on-the-floor)
Clap:  . . . . X . . . . . . . X . . .
Hat:   . . X . . . X . . . X . . . X .   (off-beat 8ths)
OpHat: . X . . . X . . . X . . . X . .   (between beats)
```
- Kick: vel 110, locked on grid
- Clap: vel 95
- Hat: tight, minimal humanize

#### DnB
```
Kick:  X . . . . . . . . . X . . . . .
Snare: . . . . X . . . . . . . X . . .
Hat:   X X X X X X X X X X X X X X X X   (16ths, fast)
```
- Snare on 2 & 4 (half-time feel at the bar level)
- Add ghost notes on snare at velocity 30-50

### 4. Humanize

After writing, apply genre-appropriate humanization:

- Lo-fi: heavy (±20 velocity, ±15ms timing, 12% swing)
- Boom-bap: medium (±15 velocity, ±10ms, 6-8% swing)
- House/Techno: minimal (±5 velocity, ±2ms, 0% swing)
- Trap: moderate on hats, tight on kick/snare
- DnB: tight on kick/snare, loose on hats

### 5. Add fill (optional)

If user wants a 2-bar pattern with fill:
- Bar 1: main pattern
- Bar 2: same, but last 1-2 beats replaced with a fill (snare roll, tom run, hat stutter)

### 6. Confirm + write

Summarize: "Lo-fi pattern, 90 BPM. Kick on 1+3, snare on 5+13, 8th hats with 12% swing. ±15 velocity, ±15ms timing. Apply?"

## Don'ts

- Don't write 100% on-grid for any genre except minimal techno or hard EDM.
- Don't overdo ghost notes (>4 per bar starts to clutter).
- Don't apply genre defaults if the user gave a specific tempo — respect their tempo.
- Don't write more than 8 bars in one shot — give the user a section to evaluate.
