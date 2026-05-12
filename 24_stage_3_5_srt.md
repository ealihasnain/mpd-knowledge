---
id: 24_stage_3_5_srt
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.5]
---

# Stage 3.5 — SRT Captions

## Outputs (3 files)

- `05_Captions_v1.srt` — cue-level (≤2 lines, ≤42 chars/line per cue)
- `05_CaptionsWord_v1.srt` — word-level (1 word per cue)
- `05_Words_v1.json` — word timestamps with confidence

All saved to `D###_TopicShort\`.

## Producer's role

Browser-manual via mpd-srt. Producer issues instructions, waits for confirmation, auto-writes log + progress.md.

## Instruction template

```
═══════════════════════════════════════════════════════
STAGE 3.5 — SRT CAPTIONS for D### [TopicShort]
═══════════════════════════════════════════════════════

1. Open https://ealihasnain.github.io/mpd-srt/ in browser.

2. Upload: 04_VoiceAudio_v1.mp3 from D###_TopicShort\

3. Settings:
   - Model: whisper-large-v3
   - Language: English (en)
   - Translation: OFF
   - Output: all three (cue-level SRT, word-level SRT, JSON)
   - Cue formatting: ≤2 lines per cue, ≤42 chars per line

4. Click "Transcribe" → wait (large-v3 takes ~1 min per 4 min audio)

5. When complete, download all three files. Rename if needed:
   - `05_Captions_v1.srt`
   - `05_CaptionsWord_v1.srt`
   - `05_Words_v1.json`

6. Save all three to D###_TopicShort\

7. CRITICAL — manual review of `05_Captions_v1.srt`:
   - Open in Notepad
   - Scan for proper-noun errors (Whisper struggles with names, brand
     names, MPD-specific terms)
   - Common fixes for this channel:
     - "money patterns decoded" → "MoneyPatternsDecoded" (or just "MPD")
     - financial brand names (correct spelling)
     - numbers spelled out in script but Whisper may insert digit form;
       leave as Whisper transcribed (digit form is fine in captions)
   - DO NOT edit word-level SRT or JSON (those drive 3.6 iconTimes)

8. Reply in chat with:
   "captions done, [N] cues, manual corrections: [list any] or [none]"
═══════════════════════════════════════════════════════
```

## Producer validation (G5)

After user confirms:
1. Sanity check: number of cues roughly = (word count / 8) ± 20%.
2. Auto-write log: `- D###: WORKED — Whisper clean, N cues | FIX — [proper noun corrections, if any] | HYP — [if many corrections, maybe pre-edit script with phonetic hints]`
3. Auto-update progress.md → 3.5 passed.

## Failure modes

- **Whisper translates instead of transcribes:** language setting wrong. Re-run with `en` forced.
- **Word-level JSON malformed:** rare; re-download. If persistent, fall back to ffmpeg + whisper-cli locally (deferred to v1.4).
- **Cue overlap >10ms:** auto-handled by mpd-srt's post-processor; if user reports overlaps, ask for the SRT line numbers.
