---
id: 26_stage_3_7_avmerge
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.7]
---

# Stage 3.7 — A+V Merge

## Output

- `08_FinalMaster_v1.mp4` — H.264/AAC, 1920×1080, 24fps, audio normalized

Saved to `D###_TopicShort\`.

## Prerequisite

Before 3.7, you need `07_MergedVideo_v1.mp4` — a silent video export of the
Stage 3.6 HTML. This is currently a manual step:

### Generating 07_MergedVideo_v1.mp4 (manual screen recording)

1. Open `06_VideoHTML_v#.html` in Chrome (fullscreen, F11).
2. Use OBS Studio or similar:
   - Source: Window/Display capture of the browser
   - Resolution: 1920×1080
   - Framerate: 24fps
   - Encoder: H.264 hardware (NVENC/QuickSync) or x264 medium
   - Audio: muted (we add audio in 3.7)
3. Trigger the HTML's start (page-load animations begin)
4. Record duration = your audio duration (from 3.4 reporting)
5. Save as `07_MergedVideo_v1.mp4` to `D###_TopicShort\`

(Future v1.4: automate via Playwright/Puppeteer. Out of v1.3 scope.)

## Producer's role for 3.7

Browser-manual via mpd-av-merger. Producer issues instructions, waits.

## Instruction template

```
═══════════════════════════════════════════════════════
STAGE 3.7 — A+V MERGE for D### [TopicShort]
═══════════════════════════════════════════════════════

PREREQ: 07_MergedVideo_v1.mp4 must exist in D###_TopicShort\
        If not, complete screen capture per stage prompt first.

1. Open https://ealihasnain.github.io/mpd-av-merger/ in browser.

2. Upload inputs:
   - Video slot: 07_MergedVideo_v1.mp4
   - Audio slot: 04_VoiceAudio_v1.mp3

3. Settings (defaults if v3+ build):
   - Mode: Replace audio (drops video's silent track, uses MP3)
   - Codec: Stream-copy (no re-encode unless format mismatch)
   - Audio offset: 0 seconds
   - Trim to shortest: ON

4. Click Merge → wait for ffmpeg.wasm to process (~10–60s).

5. Download the result.

6. Sync verification (G8 check) — open the result, scrub to 3 random points:
   - Pick a moment where a specific word is spoken (e.g., a $ amount)
   - Verify the matching iconTime visual is on screen within ±80ms
   - Try 3 different timestamps spread across the video
   If any miss by >80ms, re-merge with offset adjustment (try +/-0.05s).

7. Loudness verification (G9 check) — the merger reports final integrated
   LUFS. Should be -14.0 ± 0.5.

8. Rename to: `08_FinalMaster_v1.mp4`

9. Save to: C:\Users\ali.hasnain\OneDrive\3. MoneyPatternsDecoded\D###_TopicShort\

10. Reply with: "merge done, duration M:SS, LUFS -NN.N, sync ±NNms at probes"
═══════════════════════════════════════════════════════
```

## Validation on user response

| Metric | Pass criteria | Fail action |
|---|---|---|
| Sync | ≤ 80ms at all 3 probes (G8) | Re-merge with offset adjustment; if persistent, the underlying HTML/audio mapping in 3.6 was off — return to 3.6 |
| LUFS | -14.0 ± 0.5 (G9) | Re-export 04_VoiceAudio with stricter LUFS targeting |
| Duration | matches 04_VoiceAudio ± 1s | Investigate trim or codec issue |

## Auto-write on completion

3.7 → passed, 36_learnings_3_7.md log line, 3 downloads.

## Failure modes

- **Stream-copy fails** due to codec mismatch between video and audio. Switch merger to re-encode mode (slower, ~3min for 8-min content). Note in learning log.
- **Sync drift across video:** typically caused by variable framerate in the screen recording. Re-record OBS with CFR (constant framerate) 24fps locked.
- **LUFS off after merge:** rare with stream-copy. If using re-encode, ensure mpd-av-merger's `loudnorm` filter is enabled.
