---
id: 36_learnings_3_7
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.7]
---

# Learnings — Stage 3.7 (A+V Merge)

**Auto-read** at stage start (Active Rules → gate input).
**Auto-written** at stage end.

## Active Rules

- [SEED] Use mpd-av-merger browser tool: https://ealihasnain.github.io/mpd-av-merger/
- [SEED] Settings (LOCKED):
    - Mode: replace audio
    - Codec: stream-copy (no re-encode unless format mismatch)
    - Audio offset: 0 seconds (assumes Stage 3.6's MergedVideo already has audio anchored to its visual)
    - Trim to shortest: ON
- [SEED] Inputs: `07_MergedVideo_v1.mp4` (silent rendered video from Stage 3.6) + `04_VoiceAudio_v1.mp3` (mixed audio).
- [SEED] Output: `08_FinalMaster_v1.mp4` to `D###_TopicShort\`.
- [SEED] G8 verification: sync probe at 3 random caption-cue timestamps. Word onset (per word-SRT) vs visual icon trigger delta ≤ 80ms. If > 80ms, re-render with adjusted offset.
- [SEED] G9 verification: final master integrated loudness = -14.0 ± 0.5 LUFS, peaks ≤ -1.0 dBTP. The browser tool's ffmpeg `loudnorm` filter enforces; check output report.
- [SEED] If stream-copy fails due to format mismatch, switch to re-encode mode with H.264 + AAC. Note in Episode Log (slower path, but reliable fallback).

## Episode Log (newest first)

*(No entries yet.)*

## Pending Promotions

*(No pending promotions yet.)*
