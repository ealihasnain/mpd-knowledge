---
id: 99_changelog
version: 1.0
updated: 2026-05-10
applies_to_stages: [all]
---

# MPD Knowledge Base — Changelog

## v1.0 — Initial bootstrap (Phase 2 — 2026-05-10)

- Repo created from MPD Automation Master Spec v1.3.
- Atomic .md files split from prior monolith sources:
  - v1.1 Master Spec → 02_naming_convention, 03_workspace_layout, 08_gates_G1_G11
  - 1_1a_voice.md → 01_overview, 04_voice_canon, 10_style_tokens
  - 1_1b_corpus.md → 06_corpus_index
  - 1_1c_calendar.yml → 07_calendar_format (schema doc) + calendar copied as-is
  - mpd-producer SKILL.md → 11_critique_checklist_global, 20–29 stage prompts (v0.1 drafts)
- Empty learning log schemas (30–39) seeded.
- Phase 5 placeholders: 05_voice_blocklist, 09_gate_G12_slop (status: 0.1 seed).
- Phase 4 placeholders: 20–29 stage prompts (status: 0.1 drafts; full content
  migration deferred to Phase 4).
 
## v1.0 → v1.1 — Phase 5 + 6 prep (2026-05-11)

### Updated
- `05_voice_blocklist.md` (v0.1 → v1.0): Channel-specific Hard Ban additions
  across 4 categories (AI-template clichés, padding/filler, overused
  transitions, aesthetic-corrupted vocabulary). Channel-specific allowlist
  preserved. Sentence-opening classification table (Q/N/SV/IM/AN) for G12
  criterion 4.
- `09_gate_G12_slop.md` (v0.1 → v1.0): Soft-fail latitude added for
  subjective criteria (rhythm variety, voice fingerprint). Calibration plan
  for post-D003 review.

### Seeded
- `30_learnings_3_1.md` through `39_learnings_3_10.md`: Active Rules
  populated from voice canon + spec gates + v1.1-era lessons. Episode Log
  + Pending Promotions sections empty (populate during D001 ship onward).

### Total impact
- 2 atomic refs updated (Phase 5)
- 10 learning logs seeded (Phase 6)
- 12 files total, ready to push.

**Manual step for user:** append this section content to existing
`99_changelog.md` before pushing (preserves prior changelog history).
