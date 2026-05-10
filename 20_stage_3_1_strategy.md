---
id: 20_stage_3_1_strategy
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.1]
---

# Stage 3.1 — Strategy Brief

**Status:** v0.1 draft. Full prompt content migrated from existing producer
skill references in Phase 4.

## Output

`01_StrategyBrief_v#.html`

## Gates applied

G1, U1–U6, G12

## Critical requirements

≥ 80 data points, VER/EST/ATT tags on each, hidden-pattern angle, reframe moment, 7–9 chapters, visual asset prescriptions, Open Loop Hook + Callback Number

## Atomic refs fetched at start of stage

```
- `02_naming_convention.md`
- `04_voice_canon.md`
- `06_corpus_index.md`
- `08_gates_G1_G11.md`
- `09_gate_G12_slop.md`
- `11_critique_checklist_global.md`
- `20_stage_3_1_strategy.md`
- `30_learnings_3_1.md`
```

## Source

Detailed prompt content for this stage will be migrated from the existing
`mpd-producer/references/3_3_1_*.md` files during
Phase 4 (skill rewire). Until then, the producer skill should fall back
to its embedded stage logic.

## Inputs (from prior stage)

Topic + pillar + keyword (from queue.yml)

## Auto-write to learning log on completion

After stage emission (gates passed or soft-failed), producer appends one line
to `30_learnings_3_1.md` Episode Log:

```
- D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>
```

Returns the regenerated learning .md as a download alongside the artifact.
