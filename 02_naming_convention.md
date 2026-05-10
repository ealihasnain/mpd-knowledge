---
id: 02_naming_convention
version: 1.0
updated: 2026-05-10
applies_to_stages: [all]
---

# Naming Convention

Strict, mechanical, applied to every artifact.

## Master pattern

```
MPD_D###_TopicShort_ArtifactType_v#.ext
```

| Component | Rules | Example |
|---|---|---|
| `MPD` | Literal prefix, always | `MPD` |
| `D###` | 3-digit day number from `queue.yml` `week` field, zero-padded | `D001`, `D012`, `D147` |
| `TopicShort` | PascalCase, ≤16 chars, no spaces/punctuation | `PayYourselfWrong`, `TenPercentLie` |
| `ArtifactType` | Canonical type from table below | `StrategyBrief`, `VoiceScript` |
| `v#` | Version, integer, increments on patch | `v1`, `v2`, `v3` |
| `ext` | File extension, lowercase | `.html`, `.mp3`, `.mp4`, `.png` |

## Artifact types (canonical)

| Stage | ArtifactType | Extension |
|---|---|---|
| 3.1 | `StrategyBrief` | `.html` |
| 3.2 | `VoiceScript` | `.html` |
| 3.2 | `ChaptersTable` | `.txt` (named `1_4_MPD_ChaptersTable_D###.txt`) |
| 3.3 | `VoicePart1`, `VoicePart2` | `.mp3` |
| 3.4 | `VoiceAudio` | `.mp3` |
| 3.5 | `Captions` | `.srt` |
| 3.5 | `CaptionsWord` | `.srt` |
| 3.5 | `Words` | `.json` |
| 3.6 | `VideoHTML` | `.html` |
| 3.6 | `MergedVideo` | `.mp4` (silent video export from VideoHTML) |
| 3.7 | `FinalMaster` | `.mp4` |
| 3.8 | `Thumbnail` | `.png` (1280×720) |
| 3.9 | `UploadPack` | `.html` |

## Workspace ordering prefix

Inside `D###_TopicShort\` folders, files have a numeric prefix for ordering:

```
01_StrategyBrief_v1.html       ← canonical name: MPD_D###_TopicShort_StrategyBrief_v1.html
02_VoiceScript_v1.html
03_VoicePart1_v1.mp3
04_VoiceAudio_v1.mp3
…
```

The numeric prefix is workspace ordering only. Canonical full filenames per
the master pattern are what get used in upload packs and any external reference.

## Version increments

- `v1` for fresh stage output that passed gates first try.
- `v2` after `mpd-patch` is invoked on `v1`.
- `v3` after a second patch.
- New episode = reset to `v1`.

## Day numbering (D###)

- Source: `week` field in `queue.yml` for the active episode.
- Calendar (`1_1c_calendar.yml`) maps calendar dates to D-numbers.
- `D001` is the first ever production episode (May 1, 2026).

## Folder naming

```
D001_PayYourselfWrongD012_TaxRefundTrap```

Folder name = `D###_TopicShort\` (no `MPD_` prefix on folders, just on files inside).
