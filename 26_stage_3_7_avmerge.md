---
id: 26_stage_3_7_avmerge
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.7]
---

# Stage 3.7 — A+V Merge

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`08_FinalMaster_v#.mp4`

## Gates applied

G8, G9

## Critical requirements

Use mpd-av-merger browser tool (ffmpeg.wasm). Replace audio mode, stream-copy, 0s offset, trim-to-shortest. Sync ±80ms at 3 random probes, integrated −14 ± 0.5 LUFS.

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `26_stage_3_7_avmerge.md`
- `36_learnings_3_7.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_7_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

VideoHTML rendered MergedVideo MP4 + VoiceAudio MP3

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `36_learnings_3_7.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
