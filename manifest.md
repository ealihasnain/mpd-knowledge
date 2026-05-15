---
id: manifest
version: 2.0
updated: 2026-05-14
purpose: Bootstrap URL list. Primary URLs via raw.githubusercontent.com (returns file body as plaintext — URLs inside become immediately allowlisted for subsequent web_fetch calls in the same chat). api.github.com used only for post-push verification (Section 8 of Project Custom Instructions) where CDN freshness matters and base64-wrapping is acceptable.
---

# MPD Knowledge Base — URL Manifest

This file is the single bootstrap point. Project Custom Instructions
contain only the raw URL of this file. Producer fetches it at chat
start via raw.githubusercontent.com; every URL listed below becomes
fetchable for any subsequent file in the same session — no manual
URL injection, no base64 unwrap, no chain-break at cross-repo hops.

**Primary URL pattern:**
`https://raw.githubusercontent.com/<owner>/<repo>/main/<path>`

Raw returns plaintext. Strip frontmatter before parsing.

Cache lag: 5–15 min staleness window for previously-cached files
after a push (newly-created files propagate within seconds). For
just-pushed files where freshness is required, see the verification
fallback at the bottom of this file and Section 8 of Project Custom
Instructions.

---

## mpd-knowledge — operational state (frequently updated)

- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/progress.md
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/queue.yml

## mpd-knowledge — pre-stage references

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

## mpd-knowledge — stage prompts

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

## mpd-knowledge — learning logs (auto-updated per stage)

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

## mpd-knowledge — calendar & changelog

- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/1_1c_calendar.yml
- https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/99_changelog.md

## mpd-episodes — active episode index

Active episode:
- https://raw.githubusercontent.com/ealihasnain/mpd-episodes/main/D001_PayYourselfWrong/index.md

Each per-episode `index.md` lists raw URLs for that episode's
artifacts (StrategyBrief, VoiceScript, audio, SRT, VideoHTML,
thumbnail, upload pack). When a new episode is started, producer
creates `D###_TopicShort/index.md` in mpd-episodes and updates the
Active episode line above.

---

## Verification fallback (api.github.com — Section 8 use only)

Post-push freshness verification (Section 8 of Project Custom
Instructions) uses api.github.com directly because raw has a 5–15 min
CDN lag for updated files that would falsely flag fresh pushes as
not-landed. api is fresh-on-write.

Derivation rule (mechanical, no separate URL list needed):
`raw.githubusercontent.com/<r>/main/<p>`  ⇄  `api.github.com/repos/<r>/contents/<p>`

The manifest's own api URL (used by Section 8 to verify a manifest
push):
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/manifest.md

api.github.com returns JSON with `.content` base64-encoded (60-char
line wrap with `\n` separators). Parse `.content`, base64-decode,
strip frontmatter. Rate limit: 60/hr/IP unauthenticated.

---

## Adding a new file

1. Push the new file to the repo.
2. Append its **raw URL** to the appropriate section above.
3. Bump this file's `version` and `updated` in frontmatter.
4. Push the updated manifest.

Next chat will see fresh content automatically — newly-created files
propagate to raw CDN within seconds. (Cache lag only affects
*previously-cached* files that were just updated, which is the
verification scenario covered by Section 8.)

## Starting a new episode

1. Create folder `D###_TopicShort/` in mpd-episodes.
2. Create `index.md` listing raw URLs for that episode's artifacts.
3. Update the "Active episode" line above: replace prior episode's
   `index.md` URL with the new one.
4. Bump manifest `version` and push.

## Migration note (v1.x → v2.0)

v1.x listed api URLs as primary and duplicated raw URLs as fallback.
This caused a chain-break: api responses are base64-wrapped JSON, so
URLs inside the manifest body never appeared as plaintext to
web_fetch's allowlist, and cross-repo hops (mpd-knowledge → mpd-episodes
→ artifacts) required manual user paste-injection. v2.0 lists raw URLs
as primary (returns plaintext, URLs propagate automatically) and keeps
api purely for Section 8 post-push verification where freshness matters.
