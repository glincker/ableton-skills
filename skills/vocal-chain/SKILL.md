---
name: vocal-chain
description: Use when the user has recorded vocals and wants a processing chain set up. Examples - "set up my vocal chain", "process this vocal", "make the vocal sit in the mix", "give me a pop vocal chain", "make this rap vocal aggressive".
---

# Vocal Chain

Set up a vocal processing chain on the vocal track. Stock Ableton plugins by default; user can swap to third-party manually.

## Workflow

### 1. Identify the vocal style

Ask if not given:

| Style | Sonic goals |
| --- | --- |
| Pop lead | Bright, present, controlled, clean |
| Rap (modern) | Aggressive, in-your-face, heavy compression |
| Indie/lo-fi | Warm, slightly distant, character preserved |
| R&B | Smooth, lush, with subtle pitch correction |
| Cinematic/spoken word | Intimate, breathy, minimal processing |
| Backing vocals | Sit behind the lead — duller, narrower, ducked |

### 2. Inspect the recording

`get_track_info` for the vocal track. Check:
- Peak level (should be -6 to -3 dB ideally)
- Any existing devices (don't blow them away)
- Mono or stereo (vocals are usually mono)

If peaks are red or the recording is below -20 dB, flag it: "Re-record at proper gain first; processing won't fix a bad recording."

### 3. Build the chain

#### Order matters. Standard order:

1. **Gate / Noise reduction** (only if needed)
2. **Subtractive EQ** (cut problems)
3. **De-esser** (tame harsh sibilance)
4. **Compressor 1** (peak control, fast)
5. **Compressor 2** (leveling, slow)
6. **Additive EQ** (boost desired frequencies)
7. **Saturation** (optional, for character)
8. **Pitch correction** (Auto-Tune / Melodyne / Vocal Pitch — if needed)
9. **Reverb send** (to a return, not in-line)
10. **Delay send** (to a return, not in-line)

#### Pop lead chain (stock Ableton)

| Slot | Plugin | Settings |
| --- | --- | --- |
| 1 | EQ Eight | HPF 80 Hz, cut -3 dB at 250 Hz, cut -2 dB at 4k (problem range) |
| 2 | Multiband Dynamics | De-ess range 5-9 kHz, threshold -25 dB, ratio 4:1 |
| 3 | Compressor | Ratio 4:1, attack 5 ms, release 60 ms, threshold for 4-6 dB GR on peaks |
| 4 | Glue Compressor | Ratio 2:1, slow attack, auto release, 1-2 dB GR (leveling) |
| 5 | EQ Eight | +2 dB at 100 Hz (warmth), +2 dB at 5 kHz (presence), +2 dB at 12 kHz (air) |
| 6 | Saturator (optional) | Drive 2-3 dB, Soft Clip mode |
| Send A | Hall reverb | 15-20% wet, pre-delay 30-50 ms |
| Send B | Ping Pong delay | 1/8 dotted, 15-20% wet, feedback 25% |

#### Rap (modern, aggressive) chain

| Slot | Plugin | Settings |
| --- | --- | --- |
| 1 | EQ Eight | HPF 100 Hz, surgical cuts on resonances |
| 2 | Multiband Dynamics | De-ess 5-9 kHz, ratio 6:1 (aggressive) |
| 3 | Compressor | Ratio 6:1, attack 3 ms, release 40 ms, GR 6-8 dB |
| 4 | Compressor 2 | Ratio 3:1, attack 30 ms, release auto, GR 2-3 dB |
| 5 | EQ Eight | +3 dB at 5 kHz (aggression), +2 dB at 200 Hz (chest) |
| 6 | Saturator | Drive 4-6 dB, Soft Sine mode (mild distortion) |
| Send A | Plate reverb (Ableton Reverb in Plate algorithm) | 8-12% wet, short pre-delay |
| Send B | Slap delay | 1/16 single repeat, 10% wet |

#### Indie / lo-fi chain

| Slot | Plugin | Settings |
| --- | --- | --- |
| 1 | EQ Eight | HPF 70 Hz, gentle |
| 2 | Compressor | Ratio 3:1, slow attack 30 ms, release 80 ms, GR 3-4 dB |
| 3 | Saturator | Drive 3-5 dB, Tape mode (warmth) |
| 4 | EQ Eight | -1 dB at 8 kHz (slightly dull), gentle |
| 5 | Vinyl Distortion or Cabinet | Subtle, for lo-fi character |
| Send A | Vintage spring reverb | 25-30% wet (more present) |

### 4. Apply with confirmation

Show the proposed chain. Confirm before writing. Apply each device in order.

### 5. Listen and tune

After applying, the user listens. Adjust based on feedback:

- Too dark? → Add 1-2 dB at 10-12 kHz
- Too bright/harsh? → Reduce de-ess threshold, or cut at 4-5 kHz
- Pumping too obvious? → Reduce compressor ratio or threshold
- Sibilance still strong? → De-ess threshold lower or range tighter

## Don'ts

- Don't auto-tune without asking — many vocals are intentionally raw.
- Don't apply 8+ dB of compression in one stage; use two stages instead (peak compress + leveling).
- Don't put reverb in-line — always on a send.
- Don't load expensive third-party plugins by default. Stock chain works for 80% of cases.
- Don't pitch-correct outside the song's key without confirming the key first.
