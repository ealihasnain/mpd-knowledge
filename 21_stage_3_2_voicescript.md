---
id: 21_stage_3_2_voicescript
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.2]
---

# Stage 3.2 — Voiceover Script

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`02_VoiceScript_v#.html`

## Gates applied

G2, G3, G3a, U1–U6, G12

## Critical requirements

Numbers echo Strategy Brief data points, TTS-safe (no ellipses/em-dashes/numerals), each part ≤ 5,000 chars, emotion tag per sentence, 4 emotional variation moments, no sentence > 28 words, data density ≥ 3 numbers/chapter

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `04_voice_canon.md`
- `05_voice_blocklist.md`
- `08_gates_G1_G11.md`
- `09_gate_G12_slop.md`
- `11_critique_checklist_global.md`
- `21_stage_3_2_voicescript.md`
- `31_learnings_3_2.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_2_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

Strategy Brief Compact Info payload

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `31_learnings_3_2.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
