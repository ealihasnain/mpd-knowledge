---
id: 35_learnings_3_6
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.6]
---

# Learnings — Stage 3.6 (Video HTML)

**Auto-read** at stage start (Active Rules → gate input).
**Auto-written** at stage end.

## Active Rules

- [SEED] Use ONLY style tokens from `10_style_tokens.md`. No off-palette colors. Off-palette = binary fail.
- [SEED] CSS variable block MANDATORY at top of `<style>`:
    `--canvas-base #E4DDD0`, `--ink #2A2520`, `--accent-primary #2DB89D`,
    `--accent-secondary #F5C518`, `--alert-reveal #E63946`, `--supporting #8BA8B5`.
- [SEED] Three fonts ONLY: Barlow Condensed 900 (headlines/stats), Barlow 400/700 (body), DM Mono 400/500 (data/code/citations). Other fonts = binary fail.
- [SEED] Paper grain overlay MANDATORY: 200×200 SVG noise, `mix-blend-mode: multiply`, `opacity: 0.5`, fixed positioning.
- [SEED] `iconTimes[]` array entries MUST reference real SRT cue timestamps from `05_CaptionsWord_v1.srt`, NOT estimates. G6 binary fail otherwise.
- [SEED] Every video HTML must include a `NEW ASSETS FOR LIBRARY` manifest section listing any newly-created portraits, country panels, brand badges, etc. for inclusion in the asset registry by Stage 3.10. G7a binary fail if missing.
- [SEED] Asset reuse from corpus library documented per chapter (which assets came from prior episodes vs which are new).
- [SEED] Chapter card animation: minimum 200ms fade-in, NEVER instant flash (causes viewer blink-skip).
- [SEED] Test render at 1920×1080 24fps before submitting to Stage 3.7. Verify no clipping, no text overflow, no animation jitter.

## Episode Log (newest first)

*(No entries yet.)*

## Pending Promotions

*(No pending promotions yet.)*
