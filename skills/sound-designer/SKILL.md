---
name: sound-designer
description: Use when the user wants to design a synth patch from scratch or modify an existing one - lead, bass, pad, pluck, lush keys, FX. Targets stock Ableton synths (Operator, Wavetable, Analog, Drift). Examples - "make me a wide supersaw lead", "design a sub bass", "give me a lush pad like Olafur Arnalds".
---

# Sound Designer

Build synth patches from a description. Stock Ableton synths only — Operator (FM), Wavetable (wavetable + FM), Analog (subtractive), Drift (modern subtractive). User can swap to a third-party synth manually after.

## Workflow

### 1. Pick the right synth

| Sound type | Best synth | Why |
| --- | --- | --- |
| Sub bass, 808 | **Operator** (sine + saturation) or Drift | Pure low end, easy to control |
| Reese / Massive bass | **Wavetable** | Detuned saws + filter movement |
| Pluck / staccato | **Operator** | Fast envelopes, FM bite |
| Wide supersaw | **Wavetable** (saw table, unison 7+) | Native unison + detune |
| Lush pad | **Wavetable** (LP filter + slow envelopes) | Movement + filter LFO |
| Acoustic-y / felt | **Drift** + tape simulation | Warm character |
| Vintage analog lead | **Analog** | Authentic voicing |
| Bell / mallet | **Operator** (FM ratios) | Inharmonic partials |

### 2. Set base parameters

For each patch type, here's the starting point:

#### Sub bass (Operator)
- Algorithm: A only (single sine)
- Osc A: Sine, level 0 dB
- Filter: off
- Amp env: Attack 0, Decay 0, Sustain 1.0, Release 0.1
- Glide: 50ms (mono mode)

#### Wide supersaw (Wavetable)
- Osc 1: Saw 1 wavetable
- Unison: 7 voices, detune 25-35
- Filter 1: LP24, cutoff 80%, resonance 15%, env 30%
- Filter env: Attack 0, Decay 400ms, Sustain 50%, Release 200ms
- Amp env: A 5ms, D 200ms, S 80%, R 300ms

#### Lush pad (Wavetable)
- Osc 1: Choir/Vocal wavetable
- Osc 2: Saw, detuned -7 cents
- Filter LP24, cutoff 60%, resonance 10%
- Filter LFO: triangle, rate 0.1 Hz, amount 25%
- Amp env: A 800ms, D 1500ms, S 70%, R 2000ms
- Add chorus + Hall reverb on the chain

#### Pluck (Operator)
- Algorithm: B→A
- Op B (modulator): Ratio 2.0, fixed level
- Op A: Sine, level 0
- Filter: LP, cutoff 70%, env amount 40%
- Filter env: A 0, D 80ms, S 0%, R 100ms
- Amp env: A 0, D 200ms, S 0%, R 100ms

### 3. Add character with effects

After the synth, append:

- **Saturator** before filter (drive 3-6 dB) for warmth
- **Chorus** for width on pads/leads
- **Auto Filter** with LFO mod for movement
- **Reverb send** to Return A (Hall) — typical 20-30% on pads, 10-15% on leads
- **Delay send** to Return B (Ping Pong) — 15-20% on plucks/leads
- **EQ Eight** at the end of chain — surgical cut at any harsh resonance

### 4. Verify

Read back the parameters, confirm:
> *"Wavetable supersaw lead with 7-voice unison at 30 detune, LP24 filter at 80% with light env motion, chorus + 25% reverb send. Save as 'Wide Lead'?"*

### 5. Save preset (if MCP supports)

`save_device_preset` to user's User Library if available. Otherwise tell user to save manually with Cmd+S on the device.

## Don'ts

- Don't recommend third-party synths the user might not have (Serum, Massive, Diva, etc.) by default.
- Don't max out resonance — anything above 70% on Wavetable's filter risks self-oscillation that masks the patch.
- Don't load presets without inspecting first; the user may have favorites already on the track.
- Don't apply more than 6 effects in one chain — clarity over saturation.
