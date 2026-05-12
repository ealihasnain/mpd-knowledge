---
id: 23_stage_3_4_audiomix
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.4]
---

# Stage 3.4 — Audio Mix

## Output

- `04_VoiceAudio_v1.mp3` — joined + processed audio, single file

Saved to `D###_TopicShort\`.

## Producer's role

Browser-manual via mpd-audiomixer. Producer outputs instruction block,
waits for user confirmation, auto-writes learning log + progress.md.

## Instruction template

```
═══════════════════════════════════════════════════════
STAGE 3.4 — AUDIO MIX for D### [TopicShort]
═══════════════════════════════════════════════════════

1. Open https://ealihasnain.github.io/mpd-audiomixer/ in browser.

2. Upload inputs (drag-drop or use upload button):
   - Slot 1: 03_VoicePart1_v1.mp3
   - Slot 2: 03_VoicePart2_v1.mp3
   Order matters — Part 1 first, Part 2 second.

3. Apply these LOCKED settings (defaults if v6+ build):
   - Join order: 1 → 2
   - High-pass filter: 80 Hz
   - Trim leading silence: ON
   - Trim trailing silence: ON
   - Auto-level (LUFS targeting): ON
   - Target LUFS: -14.0
   - De-essing: ON (default intensity)
   - Room tone fill: OFF
   - Boundary level match: ON
   - True-peak ceiling: -1.0 dBTP

4. Click "Process" → wait for processing (~30–60s for 8-min audio)

5. Verify the processed file's reported metrics:
   - Integrated LUFS: should be -14.0 ± 0.5
   - True peak: should be ≤ -1.0 dBTP
   - Duration: should be ≈ P1 + P2 from Stage 3.3 (within 1s)

6. Listen to the join boundary (timestamp = Part 1 duration ± 2s):
   - No click
   - No level jump > 1 dB
   - Same tonal feel (KateAsta voice consistency)
   If audible click/jump: re-process with boundary auto-match toggle OFF
   then back ON (clears any state).

7. Download. Rename if necessary to exactly: `04_VoiceAudio_v1.mp3`

8. Save to: C:\Users\ali.hasnain\OneDrive\3. MoneyPatternsDecoded\D###_TopicShort\

9. Reply in chat with:
   "audio mixed, duration M:SS, LUFS -NN.N, peak -N.N dBTP"
═══════════════════════════════════════════════════════
```

## Validation on user response

Producer parses the duration/LUFS/peak values:

| Metric | Pass criteria | Fail action |
|---|---|---|
| LUFS | -14.0 ± 0.5 (G4b) | Re-process or flag for review |
| Peak | ≤ -1.0 dBTP (G4b) | Re-process with stricter limiter |
| Duration | within 1s of P1+P2 sum | Investigate trim aggressiveness |

If pass: auto-write log + progress.md, next-step nudge for 3.5.

## Failure modes

- **Browser tool crashes on large file:** rare; mpd-audiomixer uses Web Audio API which can hit memory ceilings >10min audio. Workaround: process P1 and P2 separately, then join in a final pass.
- **OneDrive sync conflict during save:** if filename has `.conflicted` suffix, pause OneDrive briefly, rename, resume.
- **LUFS off by >1.0:** usually due to one part being significantly quieter than the other (TTS render variance). Re-run with Auto-level boundary anchoring ON.
