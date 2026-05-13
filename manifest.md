---
id: manifest
version: 1.3
updated: 2026-05-13
purpose: Bootstrap URL list. Primary URLs via api.github.com (bypasses raw CDN cache lag). Fallback raw URLs used only on 403 rate-limit from api.
---

# MPD Knowledge Base — URL Manifest

This file is the single bootstrap point. Project Custom Instructions
contain only this URL (api.github.com endpoint). Producer fetches this
file at chat start; the URLs below then become fetchable for any
subsequent file.

**Primary URL pattern (used by default):**
`https://api.github.com/repos/<owner>/<repo>/contents/<path>`

api.github.com returns JSON. Parse `.content` field, base64-decode
(handle `\n` line breaks GitHub inserts every 60 chars). The decoded
body is the file content. Strip frontmatter as before.

**Fallback URL pattern (used only on 403 from primary):**
`https://raw.githubusercontent.com/<owner>/<repo>/main/<path>`

Raw URLs return plain text. Subject to CDN cache lag; only used when
primary is rate-limited. If raw content appears stale, prompt user
and wait 5+ min before retrying primary.

---

## Operational state (frequently updated)

- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/progress.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/queue.yml

## Pre-stage references

- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/00_index.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/01_overview.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/02_naming_convention.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/03_workspace_layout.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/04_voice_canon.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/05_voice_blocklist.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/06_corpus_index.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/07_calendar_format.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/08_gates_G1_G11.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/09_gate_G12_slop.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/10_style_tokens.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/11_critique_checklist_global.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/12_rule_0_criteria.md

## Stage prompts

- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/20_stage_3_1_strategy.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/21_stage_3_2_voicescript.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/22_stage_3_3_tts.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/23_stage_3_4_audiomix.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/24_stage_3_5_srt.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/25_stage_3_6_videohtml.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/26_stage_3_7_avmerge.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/27_stage_3_8_thumbnail.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/28_stage_3_9_uploadpack.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/29_stage_3_10_library.md

## Learning logs (auto-updated per stage)

- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/30_learnings_3_1.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/31_learnings_3_2.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/32_learnings_3_3.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/33_learnings_3_4.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/34_learnings_3_5.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/35_learnings_3_6.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/36_learnings_3_7.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/37_learnings_3_8.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/38_learnings_3_9.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/39_learnings_3_10.md

## Calendar & changelog

- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/1_1c_calendar.yml
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/99_changelog.md

## Episodes (per-episode artifact indexes in mpd-episodes repo)

Active episode:
- https://api.github.com/repos/ealihasnain/mpd-episodes/contents/D001_PayYourselfWrong/index.md

Each per-episode index.md lists api.github.com URLs (with raw fallback)
for that episode's artifacts. When a new episode is started, the
producer creates `D###_TopicShort/index.md` and updates the Active
episode line above (both primary api and fallback raw).

---

## Fallback URLs (raw CDN — used only on 403 rate-limit from primary)

Derivation rule: `api.github.com/repos/<r>/contents/<p>` ↔ `raw.githubusercontent.com/<r>/main/<p>`.
All raw equivalents listed below to ensure allowlist inclusion.

### mpd-knowledge operational state
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/progress.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/queue.yml

### mpd-knowledge pre-stage references
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

### mpd-knowledge stage prompts
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

### mpd-knowledge learning logs
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

### mpd-knowledge calendar & changelog
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/1_1c_calendar.yml
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/99_changelog.md

### mpd-episodes active episode index
- https://raw.githubusercontent.com/ealihasnain/mpd-episodes/main/D001_PayYourselfWrong/index.md

---

## Adding a new file

When a new atomic ref is added to the knowledge base:
1. Push the new file to the repo.
2. Append its api.github.com URL to the appropriate primary section above.
3. Append its raw.githubusercontent.com URL to the matching Fallback section.
4. Bump this file's `version` and `updated` in frontmatter.
5. Push the updated manifest.

When a new episode is started:
1. Create folder `D###_TopicShort/` in mpd-episodes.
2. Create `index.md` with api.github.com URLs to that episode's artifacts
   (with raw fallback URLs in same file).
3. Update Episodes section above: replace prior active episode's index.md
   URL with the new one (both primary api and fallback raw equivalent).
4. Bump manifest version and push.

Next chat will see fresh content automatically — api.github.com is not
subject to raw CDN cache lag.
