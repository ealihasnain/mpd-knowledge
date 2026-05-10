---
id: 00_index
version: 1.0
updated: 2026-05-10
applies_to_stages: [all]
---

# MPD Knowledge Base — Index

Atomic reference files for the MoneyPatternsDecoded production pipeline.
This repo is fetched live by the `mpd-producer` skill at runtime — edit any
.md, push, next stage invocation reads the new version.

## Pre-stage references (loaded universally or as cross-stage gates)

- [01_overview.md](01_overview.md) — Channel mission, 5 pillars, audience, pipeline 1-pager
- [02_naming_convention.md](02_naming_convention.md) — Filename pattern for every artifact
- [03_workspace_layout.md](03_workspace_layout.md) — Windows + OneDrive folder structure
- [04_voice_canon.md](04_voice_canon.md) — KateAsta TTS settings, tone rules, sentence rhythm
- [05_voice_blocklist.md](05_voice_blocklist.md) — Banned phrases (anti-slop)
- [06_corpus_index.md](06_corpus_index.md) — 46-week content calendar (topic pool)
- [07_calendar_format.md](07_calendar_format.md) — `1_1c_calendar.yml` schema + queue logic
- [08_gates_G1_G11.md](08_gates_G1_G11.md) — 14 integrity gates
- [09_gate_G12_slop.md](09_gate_G12_slop.md) — Anti-slop quality gate
- [10_style_tokens.md](10_style_tokens.md) — CSS variables, colors, typography
- [11_critique_checklist_global.md](11_critique_checklist_global.md) — Cross-stage critique rules

## Stage prompts (loaded per active stage)

- [20_stage_3_1_strategy.md](20_stage_3_1_strategy.md) — Strategy Brief
- [21_stage_3_2_voicescript.md](21_stage_3_2_voicescript.md) — Voiceover Script
- [22_stage_3_3_tts.md](22_stage_3_3_tts.md) — TTS Render (vistatts.com browser-manual)
- [23_stage_3_4_audiomix.md](23_stage_3_4_audiomix.md) — Audio Mix (mpd-audiomixer)
- [24_stage_3_5_srt.md](24_stage_3_5_srt.md) — Captions (mpd-srt)
- [25_stage_3_6_videohtml.md](25_stage_3_6_videohtml.md) — Video HTML
- [26_stage_3_7_avmerge.md](26_stage_3_7_avmerge.md) — A+V Merge (mpd-av-merger)
- [27_stage_3_8_thumbnail.md](27_stage_3_8_thumbnail.md) — Thumbnail
- [28_stage_3_9_uploadpack.md](28_stage_3_9_uploadpack.md) — Upload Pack
- [29_stage_3_10_library.md](29_stage_3_10_library.md) — Library Update

## Learning logs (auto-read at stage start, auto-written at stage end)

- [30_learnings_3_1.md](30_learnings_3_1.md)
- [31_learnings_3_2.md](31_learnings_3_2.md)
- [32_learnings_3_3.md](32_learnings_3_3.md)
- [33_learnings_3_4.md](33_learnings_3_4.md)
- [34_learnings_3_5.md](34_learnings_3_5.md)
- [35_learnings_3_6.md](35_learnings_3_6.md)
- [36_learnings_3_7.md](36_learnings_3_7.md)
- [37_learnings_3_8.md](37_learnings_3_8.md)
- [38_learnings_3_9.md](38_learnings_3_9.md)
- [39_learnings_3_10.md](39_learnings_3_10.md)

## Operational

- [queue.yml](queue.yml) — Active episode queue (currently working topic + status)
- [1_1c_calendar.yml](1_1c_calendar.yml) — Forward-looking topic calendar
- [99_changelog.md](99_changelog.md) — Knowledge base version history
- [index.html](index.html) — Master HTML viewer (auto-fetches all .md files)

## Fetch pattern (for skills)

```
https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/<filename>
```

For example:
- `https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/02_naming_convention.md`
- `https://raw.githubusercontent.com/ealihasnain/mpd-knowledge/main/30_learnings_3_1.md`
