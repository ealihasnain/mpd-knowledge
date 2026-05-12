---
id: manifest
version: 1.0
updated: 2026-05-12
purpose: Bootstrap URL list — fetched once per chat to unlock web_fetch on all other knowledge base files.
---

# MPD Knowledge Base — URL Manifest

This file is the single bootstrap point. Project Custom Instructions
contain only this URL. Producer fetches this file at chat start; the URLs
below then become fetchable for any subsequent file.

**Base URL pattern:**
`https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/<filename>`

---

## Operational state (frequently updated)

- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/progress.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/queue.yml

## Pre-stage references (rarely change)

- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/00_index.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/01_overview.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/02_naming_convention.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/03_workspace_layout.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/04_voice_canon.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/05_voice_blocklist.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/06_corpus_index.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/07_calendar_format.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/08_gates_G1_G11.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/09_gate_G12_slop.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/10_style_tokens.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/11_critique_checklist_global.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/12_rule_0_criteria.md

## Stage prompts

- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/20_stage_3_1_strategy.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/21_stage_3_2_voicescript.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/22_stage_3_3_tts.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/23_stage_3_4_audiomix.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/24_stage_3_5_srt.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/25_stage_3_6_videohtml.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/26_stage_3_7_avmerge.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/27_stage_3_8_thumbnail.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/28_stage_3_9_uploadpack.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/29_stage_3_10_library.md

## Learning logs (auto-updated per stage)

- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/30_learnings_3_1.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/31_learnings_3_2.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/32_learnings_3_3.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/33_learnings_3_4.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/34_learnings_3_5.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/35_learnings_3_6.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/36_learnings_3_7.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/37_learnings_3_8.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/38_learnings_3_9.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/39_learnings_3_10.md

## Calendar & changelog

- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/1_1c_calendar.yml
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/99_changelog.md

---

## Adding a new file

When a new atomic ref is added to the knowledge base:
1. Push the new file to the repo.
2. Append its URL to the appropriate section above.
3. Bump this file's `version` and `updated` in frontmatter.
4. Push the updated manifest.

Next chat will see the new URL automatically.
