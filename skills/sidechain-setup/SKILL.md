---
name: sidechain-setup
description: Use when the user wants to set up sidechain compression - typically kick → bass, kick → pads, vocals → music bed. Examples - "sidechain my bass to the kick", "make the synths duck under the vocal", "add pumping to the chords".
---

# Sidechain Setup

Set up sidechain compression routing. Different DAWs/MCP servers expose this differently — read the available tools and use the simplest path.

## Workflow

### 1. Identify the source and target

- **Source** = trigger (the track that *causes* the duck) — usually kick or vocal
- **Target** = the track that *gets ducked* — usually bass, pads, or music bed

Confirm with user: "Sidechain target = bass on track 2, source = kick on track 1?"

### 2. Choose the technique

#### A. Compressor sidechain (standard for kick→bass)

- Add Compressor to the target track
- Enable sidechain input on the compressor
- Route source: select the kick track as the input
- Settings:
  - Ratio: 4:1
  - Attack: 5 ms
  - Release: 80-120 ms (release should match the tempo — at 120 BPM, 1 beat = 500ms, so 100ms ≈ 1/8 note)
  - Threshold: set so that GR shows -4 to -6 dB on each kick hit
  - Output gain: +1 to +2 dB to compensate

#### B. Glue Compressor sidechain (more musical for buses)

Same as above but using Glue Compressor — gives a more "analog" pumping sound, typical for house/EDM masters where you want musical pumping.

#### C. LFO Tool / volume automation (creative)

If the user wants extreme rhythmic pumping (EDM-style 4/4 pump):

- Use Auto Filter or a volume LFO modulator if no LFO Tool plugin
- LFO shape: sawtooth (fast attack, slow release looks like ⏐╲⏐╲)
- Sync to 1/4 notes
- Depth: -6 to -12 dB
- This is used when there's no actual kick (e.g., during a breakdown) but you want the pump feel.

#### D. Volume envelope automation (per-clip)

For surgical control on a specific section:

- Show automation on the target track
- Draw a manual ducking envelope tied to the source's hits
- Useful for vocal-driven ducking on a music bed

### 3. Apply

Use `add_device` and `set_device_parameter` to route. If the MCP server doesn't expose sidechain routing directly, write the parameters that *can* be set and tell the user the manual step:

> *"Compressor added to bass track with 4:1 ratio, 5ms attack, 100ms release. The MCP can't set the sidechain source — please click the sidechain section and select 'Kick' from the input dropdown manually. Then I'll dial in the threshold."*

### 4. Verify

After applying, ask user to play the kick + bass together. Adjust if needed:
- Pumping too obvious? → reduce ratio to 3:1 or release to 60ms
- Pumping not enough? → ratio 6:1 or threshold lower
- Bass dipping too long? → shorten release
- Bass missing the next beat? → release too long, shorten

## Don'ts

- Don't sidechain everything by default — kick→bass is universal, but pad/synth ducking is genre-specific (huge in EDM, rare in jazz).
- Don't use ratios above 8:1 unless going for a deliberate pump effect.
- Don't sidechain the master bus — that's a special-case mastering technique, not a mix move.
- Don't apply without listening — sidechain is a feel adjustment, settings depend on what the user hears.

## Quick reference table

| Use case | Ratio | Attack | Release | GR target |
| --- | --- | --- | --- | --- |
| Kick → bass (rock/pop) | 4:1 | 5 ms | 100 ms | -4 dB |
| Kick → bass (EDM pump) | 8:1 | 1 ms | 200 ms | -10 dB |
| Kick → pad/chord | 3:1 | 10 ms | 150 ms | -3 dB |
| Vocal → music bed | 2:1 | 15 ms | 300 ms | -2 dB |
| Snare → reverb tail | 3:1 | 5 ms | 80 ms | -4 dB |
