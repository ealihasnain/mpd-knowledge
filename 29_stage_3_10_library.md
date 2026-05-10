---
id: 29_stage_3_10_library
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.10]
---

# Stage 3.10 — Library Update

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`corpus + asset registry append`

## Gates applied

G11

## Critical requirements

Append new assets to 06_corpus_index.md asset library section. Bump corpus version stamp by 0.01 with one-line changelog entry. Either row count increased OR zero-asset week explicitly logged.

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `29_stage_3_10_library.md`
- `39_learnings_3_10.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_10_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

Final shipped artifacts

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `39_learnings_3_10.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
