---
id: 23_stage_3_4_audiomix
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.4]
---

# Stage 3.4 — Audio Mix

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`04_VoiceAudio_v#.mp3`

## Gates applied

G4, G4b

## Critical requirements

Use mpd-audiomixer browser tool. Defaults: HPF 80Hz, trim, autolvl, de-ess, room-tone OFF, LUFS −14. Boundary inaudible, integrated −14 ± 0.5 LUFS, peak ≤ −1.0 dBTP.

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `23_stage_3_4_audiomix.md`
- `33_learnings_3_4.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_4_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

VoicePart1 + VoicePart2 MP3s

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `33_learnings_3_4.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
