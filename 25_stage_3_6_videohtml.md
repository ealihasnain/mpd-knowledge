---
id: 25_stage_3_6_videohtml
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.6]
---

# Stage 3.6 — Video HTML

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`06_VideoHTML_v#.html`

## Gates applied

G6, G7a, G12, U1–U6

## Critical requirements

Use style tokens from 10_style_tokens.md. iconTimes[] entries map to real SRT cues. NEW ASSETS FOR LIBRARY manifest section present. Asset reuse from corpus library documented per chapter.

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `08_gates_G1_G11.md`
- `09_gate_G12_slop.md`
- `10_style_tokens.md`
- `11_critique_checklist_global.md`
- `25_stage_3_6_videohtml.md`
- `35_learnings_3_6.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_6_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

Strategy Brief + Voice Script + Words JSON + Chapters Table

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `35_learnings_3_6.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
