---
id: 22_stage_3_3_tts
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.3]
---

# Stage 3.3 — TTS Render

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`03_VoicePart{1,2}_v#.mp3`

## Gates applied

G4a

## Critical requirements

Browser-manual default — vistatts.com, paste each scriptbox part, render KateAsta preset, download MP3s. mpd-vista CLI deprecated.

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `04_voice_canon.md`
- `22_stage_3_3_tts.md`
- `32_learnings_3_3.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_3_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

Final voice script (both parts)

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `32_learnings_3_3.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
