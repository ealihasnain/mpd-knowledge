---
id: 22_stage_3_3_tts
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.3]
---

# Stage 3.3 — TTS Render

## Output

- `03_VoicePart1_v1.mp3` — Part 1 audio
- `03_VoicePart2_v1.mp3` — Part 2 audio

Both saved to `D###_TopicShort\`.

## Producer's role

This stage is **browser-manual**, not generated. Producer outputs a precise
instruction block + waits for user confirmation, then auto-writes the
learning log + progress.md.

## Instruction template (producer emits this in chat)

```
═══════════════════════════════════════════════════════
STAGE 3.3 — TTS RENDER for D### [TopicShort]
═══════════════════════════════════════════════════════

1. Open https://vistatts.com in browser (Chrome or Edge).
2. Sign in (cookies should persist; re-auth if needed).

3. Voice settings — apply these LOCKED values:
   - Voice: KateAsta
   - Voice ID: UbWKKaYfYWMB1x0WtvN7
   - Model: eleven_v3
   - Stability: 0.52
   - Similarity Boost: 0.78
   - Style: 0.12
   - Speaker Boost: ON
   - Speed: 1.0
   - Output: MP3 44.1kHz 192kbps

4. Render PART 1 first:
   - Open `02_VoiceScript_v#.html` in a text editor or browser
   - Find `<section id="scriptbox-1">`
   - Copy ONLY the contents of <pre class="script">…</pre>
   - Paste into vistatts.com input field
   - Click Render
   - When done, download MP3
   - Rename to exactly: `03_VoicePart1_v1.mp3`
   - Save to: C:\Users\ali.hasnain\OneDrive\3. MoneyPatternsDecoded\D###_TopicShort\

5. Listen to LAST ~15 seconds of Part 1. Note the tonal anchor (which
   emotion family it ends on — Curious / Reflective / High-stakes / Resolved).

6. Render PART 2:
   - Open `02_VoiceScript_v#.html`, find `<section id="scriptbox-2">`
   - Copy contents of <pre class="script">
   - Paste into vistatts.com, same settings
   - Verify Part 2's FIRST emotion tag matches the family Part 1 ended on
     (if mismatch, the script has a G3a seam violation — flag back to me
     and we'll regenerate the script)
   - Render → Download → Rename to `03_VoicePart2_v1.mp3`
   - Save to same workspace folder

7. Reply in chat with:
   "rendered, P1 = M:SS, P2 = M:SS"
   (filling in the actual duration of each MP3 — visible in vistatts UI
    after render, or check file properties in Explorer)

If render fails (CF challenge, voice not found, etc.) reply with the
exact error and we'll troubleshoot.
═══════════════════════════════════════════════════════
```

## After user reports "rendered, P1 = M:SS, P2 = M:SS"

Producer:

1. Validates total duration is roughly consistent with target word count
   (~150 wpm KateAsta cadence ≈ words ÷ 2.5 seconds; alarm if off by >20%).
2. Auto-writes 32_learnings_3_3.md Episode Log:
   `- D###: WORKED — clean render, durations P1 NN:NN P2 NN:NN | FIX — none | HYP — none`
3. Auto-updates progress.md row 3.3 → `passed`, artifact = "03_VoicePart{1,2}_v1.mp3"
4. Emits 2 downloads: updated learning log, updated progress.md
5. Next-step nudge: "Push these, then trigger `Run stage 3.4 for D###`."

## Failure modes

- **Vista CF challenge / 401:** browser-only; if user blocked, no retry path. Direct migration to ElevenLabs is the only escape (out of v1.3 scope).
- **Voice ID not found:** verify ID `UbWKKaYfYWMB1x0WtvN7` is in user's Vista account voice library.
- **Audio glitches / artifacts:** re-render with stability bumped to 0.55 (max safe), report in learning log.
- **Files saved to wrong folder:** producer's instruction explicitly names the workspace path; if user reports issue, walk through `dir` check.

## What does NOT belong in 3.3 instructions

- TTS quality assessment (deferred to 3.4 audio mix where the boundary check happens)
- Length calibration retries (if too long/short, that's a 3.2 script problem; re-do 3.2 via mpd-patch)
- Multiple voice options (KateAsta locked per voice canon)
