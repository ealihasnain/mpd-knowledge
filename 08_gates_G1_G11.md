---
id: 08_gates_G1_G11
version: 1.0
updated: 2026-05-10
applies_to_stages: [all]
---

# Integrity Gates G1–G11

Gates run as part of each stage's self-critique loop. Pass/fail determines
whether the stage emits its artifact or triggers a revision cycle.

Revision cap: **3 cycles per stage** (v1.3 — was 5 in v1.1). After cap,
soft-fail: emit best attempt, flag in critique log, continue.

## G1 — Strategy Brief data sourcing (Stage 3.1)

**Type:** Score 1–10 (must be ≥ 8) + binary requirement.

- Every data point in the Strategy Brief has a source attribution
  (URL or named publication + year).
- Total data points ≥ 80 (binary fail if not).
- VER (verified) / EST (estimate) / ATT (attributed) tags on every datapoint
  (binary fail if missing).

## G2 — Voice Script data echo (Stage 3.2)

**Type:** Binary, diff-based.

Every numeric figure in the voice script must echo a data point present in
the Strategy Brief Compact Info payload. The set diff must be empty.

Implementation: extract numbers from VoiceScript, extract numbers from
StrategyBrief Compact Info, diff. If VoiceScript contains numbers absent
from Compact Info → fail.

## G3 — Voice Script character budget (Stage 3.2)

**Type:** Binary.

Each scriptbox part (Part 1, Part 2) must be ≤ 5,000 characters including
ElevenLabs emotion tags. Vista's TTS rendering is character-billed; this
keeps cost predictable and renders fast.

## G3a — Seam tonal continuity (Stage 3.2)

**Type:** Binary.

The last sentence of Part 1 and the first sentence of Part 2 must use
emotion tags from the same family (e.g., both `<thoughtful>` or both
`<excited>`). Cross-family seams cause an audible voice flip in the merged
audio that listeners notice.

## G4 — Boundary inaudible (Stage 3.4)

**Type:** Binary, manual or auto-detected.

The seam between joined VoicePart1 and VoicePart2 audio must be inaudible
(no click, no level jump > 1 dB, no abrupt tonal shift). The mpd-audiomixer
auto boundary level match feature handles this automatically.

## G4a — TTS render success (Stage 3.3)

**Type:** Binary.

Each `03_VoicePart#_v#.mp3` exists, file size > 0 bytes, audio duration > 30s.

## G4b — Final audio loudness (Stage 3.4)

**Type:** Binary, tolerance.

`04_VoiceAudio_v#.mp3` measures **−14.0 ± 0.5 LUFS integrated** with peaks
≤ −1.0 dBTP. The mpd-audiomixer LUFS feature handles this.

## G5 — SRT timing integrity (Stage 3.5)

**Type:** Binary.

- No overlapping cues
- Last cue end ≤ audio duration + 200ms
- All word-level timestamps monotonically increasing
- No empty-text cues

## G6 — Icon trigger mapping (Stage 3.6)

**Type:** Binary.

Every entry in the VideoHTML's `iconTimes[]` array maps to a real SRT cue
where the corresponding concept is spoken. No phantom triggers (placeholder
times that point to silence or different content).

## G7a — NEW ASSETS manifest (Stage 3.6)

**Type:** Binary.

Every VideoHTML must contain a `NEW ASSETS FOR LIBRARY` manifest section
documenting any newly-created visual assets (portraits, country panels,
brand badges, etc.) for inclusion in the asset registry by Stage 3.10.

## G8 — A/V sync (Stage 3.7)

**Type:** Binary, sample-based.

After A+V merge, sync probe at 3 random caption-cue timestamps. Delta
between word onset (per word-SRT) and visual icon trigger must be ≤ 80ms.

## G9 — Final master loudness (Stage 3.7)

**Type:** Binary.

`08_FinalMaster_v#.mp4` audio track measures −14.0 ± 0.5 LUFS integrated,
peaks ≤ −1.0 dBTP (YouTube target). The ffmpeg `loudnorm` filter enforces.

## G10 — Upload pack completeness (Stage 3.9)

**Type:** Binary.

The 7 deliverables in `10_UploadPack_v#.html` are all present and within
platform limits:

1. Title (≤ 70 chars)
2. Description (≤ 5,000 chars; 3-paragraph + chapter timestamps)
3. Tags (≤ 500 chars total, 10–15 tags)
4. Thumbnail (1280×720 PNG, ≤ 2MB)
5. End-screen plan (3 elements, last 20s)
6. Pinned comment (≤ 1,500 chars)
7. Community post draft (≤ 5,000 chars)

## G11 — Library update (Stage 3.10)

**Type:** Binary.

Either:
- New assets row count in `06_corpus_index.md` increased by ≥ 1, OR
- Zero-asset week explicitly logged in changelog with reason

AND corpus version stamp incremented by 0.01.

## Gate-stage matrix

| Stage | Gates |
|---|---|
| 3.1 | G1 |
| 3.2 | G2, G3, G3a |
| 3.3 | G4a |
| 3.4 | G4, G4b |
| 3.5 | G5 |
| 3.6 | G6, G7a |
| 3.7 | G8, G9 |
| 3.8 | (style token compliance) |
| 3.9 | G10 |
| 3.10 | G11 |

All text-generating stages additionally run **G12 (slop check)** —
see [09_gate_G12_slop.md](09_gate_G12_slop.md).
