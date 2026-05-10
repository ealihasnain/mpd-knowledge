---
id: 03_workspace_layout
version: 1.0
updated: 2026-05-10
applies_to_stages: [all]
---

# Workspace Layout

Windows + OneDrive synced workspace. Path conventions are Windows-native.

## Root

```
C:\Users\<user>\OneDrive\3. MoneyPatternsDecoded\
```

## Tree

```
3. MoneyPatternsDecoded\
├── mpd-knowledge\                  (local clone of github.com/ealihasnain/mpd-knowledge)
│   ├── 00_index.md
│   ├── 01_overview.md
│   ├── …                            (all atomic refs)
│   ├── 30_learnings_3_1.md
│   ├── …                            (all learning logs)
│   ├── queue.yml
│   ├── 1_1c_calendar.yml
│   └── index.html                   (master viewer)
├── D001_PayYourselfWrong\           (one folder per episode)
│   ├── 01_StrategyBrief_v1.html
│   ├── 02_VoiceScript_v1.html
│   ├── 03_VoicePart1_v1.mp3
│   ├── 03_VoicePart2_v1.mp3
│   ├── 04_VoiceAudio_v1.mp3
│   ├── 05_Captions_v1.srt
│   ├── 05_CaptionsWord_v1.srt
│   ├── 05_Words_v1.json
│   ├── 06_VideoHTML_v1.html
│   ├── 07_MergedVideo_v1.mp4
│   ├── 08_FinalMaster_v1.mp4
│   ├── 09_Thumbnail_v1.png
│   ├── 10_UploadPack_v1.html
│   └── critique_history.md
├── D002_*\
├── _archive\                        (prior-version artifacts moved here)
│   └── 2026-05-09\
└── _local\                          (machine-specific scratch, .gitignore'd)
```

## What's NOT here anymore (v1.3 deprecation)

- `queue\` folder — replaced by `mpd-knowledge\queue.yml` (in repo, not workspace)
- `runs\` folder — per-stage chats replace per-run logs
- `learnings\` folder — replaced by `mpd-knowledge\3X_learnings_3_X.md` (in repo)
- `HALT.txt`, `RESUME_STATE.txt`, `READY_TO_PUBLISH.txt`, `CONFIRMED.txt`,
  `REVIEW_REQUIRED.txt` sentinel files — chat-only mode = no halt model

## OneDrive notes

- Workspace folder must be set to "Always keep on this device" (right-click → Always keep).
- Conflicts (rare since one machine runs at a time) auto-resolve via OneDrive's
  conflict-copy mechanism.
- Do **not** put the `mpd-knowledge\` clone inside OneDrive root if you intend
  to push from multiple machines — OneDrive sync + git can race. Recommend cloning
  to `C:\Users\<user>\OneDrive\3. MoneyPatternsDecoded\mpd-knowledge\` and
  pushing only from one primary machine.

## Companion tools (browser, not on disk)

- mpd-audiomixer: `https://ealihasnain.github.io/mpd-audiomixer/`
- mpd-srt: `https://ealihasnain.github.io/mpd-srt/`
- mpd-av-merger: `https://ealihasnain.github.io/mpd-av-merger/`
