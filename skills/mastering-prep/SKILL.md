---
name: mastering-prep
description: Use when the user is finishing a track and wants to check it's ready to send to a mastering engineer or for self-mastering. Audits headroom, peak levels, mono compatibility, frequency balance, LUFS. Examples - "is this ready to master?", "audit my mix before export", "check my levels".
---

# Mastering Prep

Pre-master audit. Confirm the mix is in a clean state for either external mastering or self-mastering. Does NOT apply final mastering — that's a separate workflow with explicit user intent.

## Workflow

### 1. Read the master bus

- `get_track_info` for master
- `get_device_parameters` for any plugins on master
- Check current peak level, RMS, LUFS if available

### 2. Run the audit checklist

For each item, mark ✅ pass or ❌ fail with the specific reading:

| Check | Target | What to look for |
| --- | --- | --- |
| **Peak level** | -3 to -6 dB | Master should have headroom — never above -1 dB |
| **No master limiter active for export-to-mastering** | Off | Mastering engineer wants raw mix; remove limiter from master |
| **No master compressor over 2 dB GR** | <2 dB | Heavy mastering compression on a pre-master is destructive |
| **LUFS integrated** | -16 to -20 LUFS for pre-master | Too loud = no headroom for mastering |
| **Mono compatibility** | All elements audible in mono | Toggle Utility's mono switch — verify nothing disappears |
| **Phase coherence** | Above 0.0 (positive) | Use Spectrum or Stereo & Phase — dips below 0 = destructive cancellation |
| **Frequency balance** | No spikes >6 dB above neighbors | Bass vs mids vs highs evenly spread |
| **Sub-bass below 40 Hz** | Cut or controlled | Anything below 30 Hz wastes headroom and clouds masters |
| **Above 18 kHz** | Cut if no musical content | Tames hiss/artifacts; saves headroom |
| **DC offset** | None | Use Utility's DC filter on the master |
| **Track-level clipping** | None | Inspect each track's meter — yellow is fine, red is not |
| **Inactive devices** | Bypass or remove | Unused devices on tracks waste CPU and confuse archiving |

### 3. Identify and report

Print the audit table with results. Lead with failures, then warnings, then passes.

> *"Audit results:*
> *❌ Master peaking at -0.8 dB — needs at least 3 dB more headroom*
> *❌ Vocals on track 3 mono-incompatible — disappears 30% in mono fold*
> *⚠️ LUFS integrated -10.2 — too loud for pre-master, drop master fader 4 dB*
> *✅ Phase coherence 0.7 — good*
> *✅ No DC offset*
> *✅ Sub-bass clean below 30 Hz*"*

### 4. Propose fixes

For each failure, propose a specific fix. Apply only on user confirmation:

- Master peaking → drop master fader by N dB
- Mono incompatibility → identify the offending track (usually a stereo widener or M/S processing pushed too far) and reduce
- LUFS too high → master fader trim
- DC offset → add Utility DC filter

### 5. Final export checklist

If user is exporting now, also confirm:
- ✅ Render quality: 24-bit, 44.1 or 48 kHz (matching project sample rate)
- ✅ Render mode: Real-time off (faster, identical output for non-resource-bound projects)
- ✅ Dither: ON for 16-bit exports, OFF for 24-bit (24-bit goes to mastering raw)
- ✅ Normalize: OFF (mastering will handle this)
- ✅ Convert to Mono: OFF (unless single-mono output requested)
- ✅ File name: includes track name, BPM, key, version (e.g., `track-name-95bpm-Cm-v3.wav`)

## Don'ts

- **Don't apply mastering chain on the user's behalf.** This skill audits, doesn't master.
- **Don't recommend external mastering tools** without asking budget and intent.
- **Don't normalize.** Normalize = peak-based loudness, irrelevant to perceived loudness, breaks headroom.
- **Don't auto-fix more than one issue at a time** — let the user listen between each.
