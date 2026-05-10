---
id: 24_stage_3_5_srt
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.5]
---

# Stage 3.5 — SRT Captions

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`05_Captions_v#.srt + 05_CaptionsWord_v#.srt + 05_Words_v#.json`

## Gates applied

G5

## Critical requirements

Use mpd-srt browser tool. Whisper large-v3, English. Outputs cue-level SRT, word-level SRT, words JSON. No overlapping cues, last cue ≤ audio + 200ms.

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `24_stage_3_5_srt.md`
- `34_learnings_3_5.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_5_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

VoiceAudio MP3

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `34_learnings_3_5.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
