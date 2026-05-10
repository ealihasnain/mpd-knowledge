---
id: 28_stage_3_9_uploadpack
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.9]
---

# Stage 3.9 — Upload Pack

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`10_UploadPack_v#.html`

## Gates applied

G10, U1–U6, G12

## Critical requirements

All 7 deliverables present and within limits: Title ≤ 70 chars, Description ≤ 5,000 chars, Tags ≤ 500 chars, Thumbnail, End-screen plan, Pinned comment ≤ 1,500 chars, Community post ≤ 5,000 chars.

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `04_voice_canon.md`
- `28_stage_3_9_uploadpack.md`
- `38_learnings_3_9.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_9_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

All prior artifacts (for description chapter timestamps + tags)

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `38_learnings_3_9.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
