---
id: 33_learnings_3_4
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.4]
---

# Learnings — Stage 3.4 (Audio Mix)

**Auto-read** at stage start (Active Rules → gate input).
**Auto-written** at stage end.

## Active Rules

- [SEED] Use mpd-audiomixer browser tool: https://ealihasnain.github.io/mpd-audiomixer/
- [SEED] Settings (LOCKED defaults):
    - High-pass filter: 80 Hz
    - Trim leading/trailing silence: ON
    - Auto-level (LUFS-target): ON
    - De-essing: ON
    - Room tone fill: OFF
    - Target LUFS: -14.0 integrated
    - True-peak ceiling: -1.0 dBTP
- [SEED] Boundary auto-match: ON (this is the safety net for G3a seam audibility).
- [SEED] After export, spot-check the seam timestamp manually. Open the merged file at the calculated boundary point (Part 1 duration). Listen for clicks, level jumps > 1 dB, tonal shifts.
- [SEED] Output: `04_VoiceAudio_v1.mp3` to `D###_TopicShort\`.
- [SEED] G4b verification: integrated loudness = -14.0 ± 0.5 LUFS, peaks ≤ -1.0 dBTP. mpd-audiomixer reports these post-export.

## Episode Log (newest first)

*(No entries yet.)*

## Pending Promotions

*(No pending promotions yet.)*
