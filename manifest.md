---
id: manifest
version: 3.0
updated: 2026-05-14
purpose: Bootstrap via github.com/blob HTML view (URLs render as plaintext anchors, no raw CDN cache lag). Content URLs routed by mutability — api.github.com for files that change frequently (operational state, knowledge refs), github.com/blob for files whose body contains URLs needing propagation (active episode index), raw.githubusercontent.com for immutable per-version artifacts. api.github.com retained for Section 8 post-push verification.
---

# MPD Knowledge Base — URL Manifest v3.0

This file is the single bootstrap point. Project Custom Instructions
contain only the **github.com/blob URL** of this file. Producer fetches
that URL at chat start; GitHub server-renders the markdown to HTML,
every URL appears as a plaintext anchor in the response, web_fetch's
allowlist captures all of them, and the rest of the chat chains
through api/raw without manual URL injection.

**Bootstrap URL:**
`https://github.com/ealihasnain/mpd-knowledge/blob/main/manifest.md`

Returns current `main` rendered as HTML. Strip the GitHub UI wrapping;
the rendered markdown body (with URLs intact) is what producer parses.

---

## URL routing by file mutability

| Class | URL pattern | Why |
|---|---|---|
| Operational state, knowledge refs | api.github.com | fresh-on-write; body has no URLs to propagate |
| Active episode index | github.com/blob | body has artifact URLs that must propagate |
| Per-version artifacts | raw.githubusercontent.com | immutable per filename+version, cache hits correct, no base64 wrapping |
| Section 8 verification | api.github.com | fastest fresh-read; bypasses render + CDN |

---

## mpd-knowledge — operational state (api, fresh-on-write)

- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/progress.md
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/queue.yml

## mpd-knowledge — pre-stage references (api)

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

## mpd-knowledge — stage prompts (api)

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

## mpd-knowledge — learning logs (api)

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

## mpd-knowledge — calendar & changelog (api)

- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/1_1c_calendar.yml
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/99_changelog.md

## mpd-episodes — active episode (github.com/blob, URLs propagate)

- https://github.com/ealihasnain/mpd-episodes/blob/main/D001_PayYourselfWrong/index.md

The per-episode `index.md` lists artifact URLs as raw.githubusercontent.com (immutable per filename+version). Fetching index.md via blob view propagates those raw URLs to the allowlist.

---

## Verification fallback (api, Section 8 use only)

The manifest's own api URL:
- https://api.github.com/repos/ealihasnain/mpd-knowledge/contents/manifest.md

Used by Section 8 of Project Custom Instructions to confirm freshness
of just-pushed content. api is fresh-on-write; bypasses both HTML
rendering and raw CDN caching. Returns JSON with `.content` base64-
encoded — decode (handling 60-char `\n` line wrap), strip frontmatter.

Rate limit: 60 requests/hr/IP unauthenticated. Typical chat: 10–20
api fetches + 1 blob fetch + a few raw fetches. Well inside budget.

---

## Per-fetch processing

| Source | Response format | Producer extracts via |
|---|---|---|
| github.com/blob (HTML) | rendered HTML page | extract markdown body; URLs in anchor tags |
| api.github.com (JSON) | JSON with base64 `.content` | base64-decode, strip frontmatter |
| raw.githubusercontent.com (plain) | plain text | strip frontmatter |

**Within a single chat, do NOT re-fetch the same URL.** Producer's
context already holds the response from the first fetch. Exception:
post-push verification per Section 8.

---

## Migration note (v1.x → v2.0 → v3.0)

v1.x: api-primary. Worked but cross-repo URL chain broke (api responses
base64-encode `.content`, so URLs inside the body never appeared as
plaintext to web_fetch's allowlist).

v2.0: raw-primary (attempted fix, never finalized). Would have failed
because raw.githubusercontent.com CDN holds blobs for days on
low-traffic paths (empirically: progress.md served v1.0 content
>24 hours after v1.3 was pushed — fresh-chat producer rendered phantom
"queued" state by faithfully reading stale raw content).

v3.0: route URLs by mutability. github.com/blob for the two files
that contain URLs needing propagation (top manifest + episode index).
api for everything that changes (operational state + knowledge refs).
raw only for immutable per-version artifacts. github.com/blob is
server-rendered per request and not subject to raw's aggressive edge
caching.

---

## Adding a new file

1. Push the new file to the repo.
2. Add its URL to the appropriate section above (route per the
   mutability table).
3. Bump `version` and `updated` in frontmatter.
4. Push the updated manifest.

## Starting a new episode

1. Create folder `D###_TopicShort/` in mpd-episodes.
2. Create `index.md` listing artifact URLs (raw form for immutable
   per-version files).
3. Update top manifest's "Active episode" section above: replace
   prior episode's index URL with the new one (github.com/blob form).
4. Bump manifest `version` and push.
