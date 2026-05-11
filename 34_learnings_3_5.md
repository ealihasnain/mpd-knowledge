---
id: 34_learnings_3_5
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.5]
---

# Learnings — Stage 3.5 (SRT Captions)

**Auto-read** at stage start (Active Rules → gate input).
**Auto-written** at stage end.

## Active Rules

- [SEED] Use mpd-srt browser tool: https://ealihasnain.github.io/mpd-srt/
- [SEED] Whisper model: large-v3. Language: English (en). Translation: OFF (we're producing English content, not translating).
- [SEED] Output ALL THREE files:
    - `05_Captions_v1.srt` (cue-level, ~8-12 chars/line ≤ 42 chars, ≤ 2 lines per cue)
    - `05_CaptionsWord_v1.srt` (word-level, 1 word per cue)
    - `05_Words_v1.json` (word timestamps with confidence scores)
- [SEED] G5 verification (auto-checked by mpd-srt):
    - No overlapping cues
    - Last cue end ≤ audio duration + 200ms
    - All word timestamps monotonically increasing
    - No empty-text cues
- [SEED] If Whisper makes obvious transcription errors (proper nouns especially), fix in `05_Captions_v1.srt` BEFORE generating video HTML. The word-level SRT and JSON typically don't need manual correction.

## Episode Log (newest first)

*(No entries yet.)*

## Pending Promotions

*(No pending promotions yet.)*
