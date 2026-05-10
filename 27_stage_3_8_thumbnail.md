---
id: 27_stage_3_8_thumbnail
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.8]
---

# Stage 3.8 — Thumbnail

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`09_Thumbnail_v#.png`

## Gates applied

Style token compliance, G12

## Critical requirements

1280×720 PNG. Use --accent-secondary (amber) for dollar/number. One face or one icon — never both. Title ≤ 5 words, Barlow Condensed 900, ≥ 96px. Contrast ratio ≥ 7:1.

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `04_voice_canon.md`
- `10_style_tokens.md`
- `27_stage_3_8_thumbnail.md`
- `37_learnings_3_8.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_8_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

Strategy Brief Compact Info + 04_voice_canon style

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `37_learnings_3_8.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
