---
name: midi-cleanup
description: Use when the user asks to humanize a MIDI part, fix voice leading, quantize notes, clean up timing, fix stuck/duplicate notes, or generally polish a MIDI clip they recorded or wrote. Examples - "humanize this hat", "voice these chords better", "the timing is too stiff", "fix the voice leading on the strings".
---

# MIDI Cleanup

You are polishing a MIDI clip the user wrote or recorded. Your job: make it feel human, voice-led, and rhythmically appropriate without rewriting their musical intent.

## Workflow

### 1. Identify the target clip

User must specify which clip. If ambiguous, ask:
> *"Which clip — the lead on track 3 or the chords on track 5?"*

Then read the clip with `get_notes_from_clip` (or equivalent). Note the note count, range, and rhythmic density.

### 2. Identify the cleanup type

Match the user's request to one of these operations:

#### A. Humanize velocity

For drums, hats, percussion, or any rhythmic part that feels stiff.

- Default range: ±10-15 velocity for hats/percussion, ±8-12 for drums
- Preserve accents: notes already at velocity >100 stay loud; notes <40 stay quiet
- Add micro-timing offsets: ±5-15 ticks (5-15 ms at 120 BPM) with a slight forward bias on off-beats for groove
- For shuffled feels: add 2-5% swing on 16th notes

#### B. Humanize timing

For piano, guitar, or string parts that sound MIDI-stiff.

- ±8-20 ms timing variance, slightly more on off-beats
- Chord notes: stagger attack 5-15 ms (top note slightly later) for "rolled" feel — only if the user wants that
- Don't humanize the downbeat of bar 1 — it's the anchor

#### C. Voice leading fix

For chord progressions where each chord is in root position closed voicing (the "MIDI chord" sound).

Rules:
- Keep the bass note in the bass voice
- Move upper voices by smallest interval to the next chord — usually a step or stay-still
- Maintain a max interval of an octave between adjacent voices (except bass-tenor which can be wider)
- For string ensembles: respect ranges (Vln1: G3-G6, Vln2: G3-D6, Vla: C3-A5, Cello: C2-C5, Bass: E1-A3)
- Avoid parallel fifths and octaves between outer voices (counterpoint baseline)

Apply by reading the current chord notes, computing the optimal voicing for each chord, and rewriting.

#### D. Quantize (intelligent)

Don't auto-quantize 100% — that destroys feel.

- Default strength: 75% to 16th-note grid
- For shuffled genres (hip-hop, lo-fi): 60-70% to a swing grid
- For tight EDM/house: 90-100% on percussion only, looser on lead/chords
- Preserve grace notes and intentional pickups (notes within 30 ms of another note ahead of grid)

#### E. Stuck/duplicate note fix

- Find notes with duration < 5 ms → delete
- Find overlapping notes with same pitch → merge or trim to non-overlap
- Find sustained notes longer than 2 bars in fast parts → suspect, ask user

### 3. Preview the changes

Before writing, summarize:

> *"I'll humanize velocity ±12 on the 32 hat notes (preserving the 4 accent hits at velocity 110), and add ±8 ms timing variance with a slight late-bias on the off-beats. Apply?"*

### 4. Apply

Use batch operations if the MCP server supports them (`set_clip_notes` with the full new note array is preferred over per-note edits — atomic, undoable in one Ctrl+Z).

### 5. Confirm result

- State what changed
- Suggest the user listen and tell you if they want more/less of the effect
- Offer to revert with one command if it doesn't feel right

## Don'ts

- **Don't change pitches** unless doing voice leading — and even then, never the melody/lead voice.
- **Don't humanize beyond ±25 velocity or ±25 ms** — that becomes noticeable as "bad timing" rather than "human."
- **Don't quantize at 100%** unless explicitly requested. Loss of feel is the #1 complaint about MIDI.
- **Don't apply voice leading to a melody.** Voice leading is for chords/pads/inner voices, not the lead line.
- **Don't touch the velocity 127 hits** — those are intentional accents.
- **Don't merge a clip you just modified.** Always leave undo on the table.

## Example

> User: "The hi-hat sounds too robotic, humanize it"

Steps:
1. Read the hat clip — 32 16th notes, all velocity 100, perfectly on grid.
2. Plan: ±12 velocity (preserve any accents), ±8 ms timing with off-beat late-bias of +3 ms, slight 4% swing.
3. Preview: "32 notes, no existing accents detected. I'll spread velocity 88-112, add 8 ms timing variance, 4% swing on off-beats. Apply?"
4. On confirm, rewrite the clip atomically.
5. Report: "Done. Listen — if it's still too tight, say 'more humanize' and I'll go to ±18 velocity."
