---
id: 99_changelog
version: 1.0
updated: 2026-05-12
applies_to_stages: [all]
---

# MPD Knowledge Base — Changelog

## v1.0 — Initial bootstrap (2026-05-10)

- Repo created from MPD Automation Master Spec v1.3.
- Atomic .md files split from prior monolith sources:
  - v1.1 Master Spec → 02_naming_convention, 03_workspace_layout, 08_gates_G1_G11
  - 1_1a_voice.md → 01_overview, 04_voice_canon, 10_style_tokens
  - 1_1b_corpus.md → 06_corpus_index
  - 1_1c_calendar.yml → 07_calendar_format (schema doc) + calendar copied as-is
  - mpd-producer SKILL.md → 11_critique_checklist_global, 20–29 stage prompts (v0.1 drafts)
- Empty learning log schemas (30–39) seeded.
- Phase 5 placeholders: 05_voice_blocklist, 09_gate_G12_slop (status: 0.1 seed).
- Phase 4 placeholders: 20–29 stage prompts (status: 0.1 drafts).

## v1.1 — Phase 5+6 prep (2026-05-10)

### Updated
- `05_voice_blocklist.md` (v0.1 → v1.0): Channel-specific Hard Ban additions
  across 4 categories. Channel-specific allowlist preserved. Sentence-opening
  classification table.
- `09_gate_G12_slop.md` (v0.1 → v1.0): Soft-fail latitude added for
  subjective criteria. Calibration plan for post-D003 review.

### Seeded
- `30_learnings_3_1.md` through `39_learnings_3_10.md`: Active Rules
  populated from voice canon + spec gates + v1.1-era lessons.

## v1.2 — D001 robustness fixes (2026-05-12)

### Critical fixes

- **20_stage_3_1_strategy.md** (v0.1 → v1.0): Full structural template for
  Strategy Brief HTML — required sections, datapoint table schema, Compact
  Info payload format, retention engineering plan.
- **21_stage_3_2_voicescript.md** (v0.1 → v1.0): Full structural template
  for Voice Script — Part 1/Part 2 scriptbox structure, TTS-safe rules,
  emotion tag conventions, character budget tracking, data echo verification.
- **22–29_stage_*.md** (v0.1 → v1.0): Detailed instruction templates for
  TTS, AudioMix, SRT, AVMerge, Thumbnail, UploadPack, Library stages.
  Producer emits structured instruction blocks for browser-manual stages.
- **12_rule_0_criteria.md** (NEW, v1.0): Formal 4-criteria topic alignment
  check with scoring and reframe-on-fail flow. Loaded by stage 3.1.
- **mpd-producer SKILL.md** (v1.3.1 → v1.3.2): Now writes progress.md at
  stage START (status: in_progress) in addition to stage END. Adds
  "redo stage X for D###" trigger. Fetch map updated to include file 12
  for stage 3.1.

### Operational fixes

- **queue.yml**: reconciled with progress.md (removed `parked_at_stage` and
  `parked_reason` fields; active episode metadata aligned).
- **index.html**: added progress.md and 12_rule_0_criteria.md to FILES list
  and sidebar nav.

### Audit outcome
- All 10 stages now have detailed structural templates (not v0.1 drafts).
- Rule 0 formalized.
- Crash-safe resume via dual progress.md writes.
- D001 launch is unblocked.
