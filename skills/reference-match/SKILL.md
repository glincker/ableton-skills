---
name: reference-match
description: Use when the user references another track they want to emulate the vibe/sound of. Examples - "make this sound like Ólafur Arnalds", "I want a Tame Impala vibe", "match the mix of Kendrick's Money Trees". Translates artist/track references into actionable production decisions.
---

# Reference Match

Translate a reference track or artist into concrete production choices. We do **not** download or analyze copyrighted audio. We use known sonic signatures and the user's own ears.

## Workflow

### 1. Identify the reference

Ask if not given: "Which track or artist? And which aspect — the arrangement, the mix, the sound design, or the overall vibe?"

### 2. Pull the sonic signature from common knowledge

Map the reference to its known characteristics. Examples:

| Reference | Signature |
| --- | --- |
| **Ólafur Arnalds** | Felt piano, string ensemble (often Spitfire), tape saturation, slow tempo (60-80), minor key, sparse arrangement, long reverb tails, microphone proximity sound |
| **Tame Impala (Currents-era)** | LinnDrum patterns, OP-1 synths, heavy chorus on guitar, vocoded vocals, sidechained bass, 60-90 BPM, vintage drum saturation |
| **Bonobo** | Live percussion + electronic drums, jazz harmony, vinyl crackle textures, mid-tempo (90-110), wide stereo, heavy use of sample chops |
| **Burial** | Vinyl/cassette texture, rain/atmosphere, pitched-up vocal samples, sub bass, garage-2step rhythm, lo-fi hihats, minor 7 chords |
| **Kendrick (DAMN era)** | 808 sub, trap hi-hats, jazz samples, vocal layering, heavy compression, mid-side EQ for vocal width |
| **Billie Eilish (early)** | Whisper vocal up close, sparse 808, finger snaps, sub-heavy mix, heavy automation, breath sounds intentionally left in |
| **Skrillex** | Heavy modulation on bass (vocal-formant LFOs), drops with stutter edits, 14k+ shimmer on leads, super-wide stereo, side-chained pump |
| **Hans Zimmer** | Massive low brass (often layered with synth), Trinity choir (low + bright), pulsing ostinatos, slow chord swells, 1-second+ reverb tails |
| **Lo-fi hip hop (Lofigirl-style)** | Wurlitzer/Rhodes, jazz chords, vinyl crackle, tape saturation, 70-90 BPM, 50% wet drums, swung 16ths |

### 3. Translate to action

For each aspect the user cares about, propose moves:

#### Arrangement
- Match section structure (Bonobo = long intros; Skrillex = constant motion)
- Match density (Billie = sparse, Skrillex = dense)

#### Mix
- LUFS target (lo-fi/Bonobo: -10 to -8 LUFS, modern pop: -8 to -6, cinematic: -16 to -14)
- Stereo width (cinematic: narrow; EDM: very wide)
- Frequency balance (trap: heavy 50-80Hz; folk/acoustic: balanced midrange)

#### Sound design
- Pick instruments matching the era/style
- Use the right synth patches (vintage analog vs modern digital)
- Match drum kit character (vinyl sample vs modern punchy)

#### Effects
- Reverb type (Hall for cinematic; Plate for vocals; Spring for surf-rock; Room for tight modern pop)
- Tape/vinyl saturation (essential for Bonobo, lo-fi, Tame Impala)
- Chorus (Tame Impala, dream pop, '80s)

### 4. Ask the user to listen and direct

Don't apply everything blindly. Pick the **3 most distinctive** elements of the reference and propose them first:

> *"Top 3 Ólafur signatures I'd start with: (1) felt piano via Spitfire Originals or stock Grand Piano with the lid closed setting + tape sat; (2) slow swelling string pad with 2-second attack + reverb send 40%; (3) tempo 70 BPM, minor key, 4/4 but with rubato feel via velocity-driven micro-timing. Apply these first, listen, then iterate?"*

### 5. Iterate

After the user listens, refine based on what's still wrong. References are inherently approximate — embrace the iteration loop.

## Don'ts

- Don't claim to "exactly clone" anyone's sound. We approximate the recipe.
- Don't download or process copyrighted audio.
- Don't recommend specific sample packs unless they're public (Splice, Output) and the user has them.
- Don't apply more than 3 reference moves before letting the user listen.

## When the reference is unfamiliar to you

If you don't know the reference: ask the user to describe what they like about it. ("Is it the drums? The vocal effect? The arrangement?") Then apply the technique that matches their description — you don't need to know the artist to translate "warm, lo-fi, jazzy chords" into action.
