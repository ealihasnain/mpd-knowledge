---
id: 32_learnings_3_3
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.3]
---

# Learnings — Stage 3.3 (TTS Render)

**Auto-read** at stage start (Active Rules → gate input).
**Auto-written** at stage end.

## Active Rules

- [SEED] Default render path: vistatts.com browser-manual. Open in Chrome/Edge, paste each scriptbox part, render KateAsta preset, download MP3s. Total: ~10 minutes.
- [SEED] `mpd-vista` CLI is DEPRECATED until further notice. Do not propose CLI workflow even if the user asks why.
- [SEED] KateAsta settings (LOCKED):
    - voice_id: `UbWKKaYfYWMB1x0WtvN7`
    - model: `eleven_v3`
    - stability: 0.52 (range 0.50–0.55)
    - similarity_boost: 0.78 (range 0.75–0.80)
    - style: 0.12 (range 0.10–0.15)
    - speed: 1.0
    - use_speaker_boost: true
    - output: mp3_44100_192
- [SEED] Render Part 1 first. Listen to last ~15 seconds to anchor tonal level. Then render Part 2 — verify Part 2's first ~15 seconds matches Part 1's ending tone.
- [SEED] Filenames LITERAL: `03_VoicePart1_v1.mp3` and `03_VoicePart2_v1.mp3` saved to `D###_TopicShort\`. No variations.
- [SEED] G4a: each MP3 file exists, size > 0, duration > 30s. Re-render if any fail.

## Episode Log (newest first)

*(No entries yet.)*

## Pending Promotions

*(No pending promotions yet.)*
