---
id: 05_voice_blocklist
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.1, 3.2, 3.6, 3.8, 3.9]
---

# Voice Blocklist — Anti-Slop Banned Phrases

**Status:** v1.0 calibrated against KateAsta canon + common finance-education
AI-template patterns. Recalibrate after D003 ships (3 episodes of real data).

## Hard ban (G12 binary fail — zero tolerance)

Generic AI-template phrasing. Any appearance in a stage 3.1, 3.2, 3.6, 3.8,
or 3.9 output = G12 fails, revision triggered.

### Category 1 — AI-template clichés

- "in today's fast-paced world"
- "in this digital age"
- "in an increasingly [adjective] world"
- "delve into" / "delving into" / "let's delve"
- "navigate the complexities"
- "navigate the world of"
- "it's important to note that"
- "it's worth noting that"
- "let's explore"
- "let's dive into"
- "let's break it down"
- "let me explain"
- "let me break this down"
- "in this article" / "in this video, we'll"
- "the truth is"
- "the reality is"
- "at the end of the day"
- "when it comes to"
- "needless to say"
- "unlock the secrets"
- "unlock the power"
- "game-changer" / "game changing"
- "in essence"
- "in conclusion"
- "to wrap things up"
- "to wrap up"
- "without further ado"

### Category 2 — Padding & filler

- "the bottom line"
- "the fact of the matter is"
- "as a matter of fact"
- "the real question is"
- "here's the thing"
- "here's where it gets interesting"
- "spoiler alert"
- "buckle up"
- "stay with me"
- "you might be wondering"
- "make no mistake"
- "long story short"
- "to put it simply"
- "to put it bluntly"
- "needless to say"

### Category 3 — Overused transitions (sentence-leading)

- "moreover,"
- "furthermore,"
- "additionally,"
- "in addition,"
- "on the other hand," (used >1× per video)
- "having said that,"
- "that being said,"

### Category 4 — Aesthetic-corrupted vocabulary

- "tapestry of"
- "embark on a journey"
- "ever-evolving"
- "ever-changing"
- "myriad of"
- "plethora of"
- "a wealth of" (when not literally about wealth)
- "a treasure trove"
- "the world of [topic]"
- "the realm of"
- "the landscape of"

## Soft watch (G12 sentence-rhythm score drop if 3+ instances)

Common but bland. Acceptable in moderation; penalize overuse.

- "essentially"
- "fundamentally"
- "ultimately"
- "actually" (when not adding contrast — i.e., when not paired with "but")
- "really" (filler usage — i.e., "really important" → just "important")
- "very" (almost always cuttable)
- "simply"
- "basically"
- "obviously"
- "clearly"

## Channel-specific allowlist (DO use — do NOT flag)

These overlap with bland writing patterns but match MPD's investigative
register when used intentionally. G12 must whitelist these:

- "Here's what's actually happening" — signature reframe phrasing
- "Most people miss this" — pillar P1 hook anchor
- "The pattern reveals" — channel anchor phrase
- "You'd think X, but actually Y" — pillar P1 setup
- "Here's what's interesting" — investigative-tone marker
- "Watch what happens when" — mechanism-explanation lead
- "Look at this number" — data-payoff marker
- "And here's the part nobody talks about" — mid-point re-hook (voice canon)

## Sentence-opening variety (G12 criterion 4)

No more than 2 chapters in a single video may open with the same construction:

| Code | Construction | Example |
|---|---|---|
| Q | Question lead | "Why do…", "What if…", "How does…" |
| N | Number/stat lead | "In 2008…", "Forty-three percent…", "$47 billion later…" |
| SV | Subject-verb lead | "Honeyfund built…", "Banks make money…" |
| IM | Imperative | "Watch what happens…", "Look at this number…" |
| AN | Anecdotal | "When Sarah opened…", "On a Tuesday in 1973…" |

3+ chapters with the same code → binary fail.

## Update protocol

When a slop phrase is observed in a real script during 3.1 or 3.2:

1. User flags via the relevant learning log (30 or 31) Episode Log line.
2. During quarterly pattern review (~every 5 episodes), recurring instances
   (3+ episodes) get promoted to a Hard Ban category here.
3. `mpd-patch` bumps version + updated frontmatter, push.

## Calibration history

| Version | Date | Note |
|---|---|---|
| 0.1 | 2026-05-10 | Initial seed (Phase 5 placeholder) |
| 1.0 | 2026-05-11 | Channel-specific additions + sentence-opening classification |
