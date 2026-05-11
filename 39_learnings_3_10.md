---
id: 39_learnings_3_10
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.10]
---

# Learnings — Stage 3.10 (Library Update)

**Auto-read** at stage start (Active Rules → gate input).
**Auto-written** at stage end.

## Active Rules

- [SEED] After every shipped episode, update `06_corpus_index.md`:
    - Mark the entry as "shipped" + add publish date
    - Append any new visual assets to the asset library section
    - Bump corpus version stamp by 0.01
- [SEED] G11 binary check: either new asset row added OR explicit zero-asset week note in changelog. Silent skip = G11 fail.
- [SEED] Cross-episode reuse tracking: if any chapter card / icon / portrait from this episode was reused from a prior episode, log it. After 10 episodes, reusable-asset density should be ≥ 30% per video (saves Stage 3.6 time).
- [SEED] Asset naming for library: `<category>_<short_name>_v#.svg` — e.g., `portrait_warrenBuffett_v1.svg`, `country_usa_v1.svg`, `brand_amex_v1.svg`. PascalCase short names.
- [SEED] Update queue.yml: move shipped episode to `recent[]` (max 10 entries, FIFO), promote next from `upcoming[]` to `active{}`.
- [SEED] Pillar tracking: count pillars across last 10 episodes; if any pillar drops below its target share by ≥ 5%, flag for next-episode pillar-prioritization. (P1 30%, P2 25%, P3 20%, P4 15%, P5 10%.)

## Episode Log (newest first)

*(No entries yet.)*

## Pending Promotions

*(No pending promotions yet.)*
