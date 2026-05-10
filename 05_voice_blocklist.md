---
id: 05_voice_blocklist
version: 0.1
updated: 2026-05-10
applies_to_stages: [3.1, 3.2, 3.6, 3.8, 3.9]
---

# Voice Blocklist — Anti-Slop Banned Phrases

**Status:** Phase 5 build — initial seed list. Refine after D003 against
real KateAsta scripts.

## Hard ban (zero tolerance, G12 binary fail)

Generic AI-template phrasing. If any of these appear in a stage 3.1, 3.2,
3.6, 3.8, or 3.9 output, G12 fails and revision is triggered.

- "in today's fast-paced world"
- "in this digital age"
- "delve into" / "delving into" / "let's delve"
- "navigate the complexities"
- "navigate the world of"
- "it's important to note that"
- "it's worth noting"
- "let's explore"
- "let's dive into"
- "in this article" / "in this video, we'll"
- "the truth is"
- "at the end of the day"
- "when it comes to"
- "needless to say"
- "unlock the secrets"
- "unlock the power"
- "game-changer" / "game changing"
- "in essence"
- "one might say"
- "moreover" (sentence-leading)
- "furthermore" (sentence-leading)
- "additionally," (sentence-leading)
- "in conclusion"
- "to wrap things up"
- "without further ado"
- "tapestry of"
- "embark on a journey"
- "ever-evolving"
- "myriad of"
- "plethora of"

## Soft watch (G12 score ≤ 7 if 3+ instances)

Common but acceptable in moderation. Score sentence-rhythm-variety down if
overused.

- "essentially"
- "fundamentally"
- "ultimately"
- "actually" (when not adding contrast)
- "really" (filler usage)
- "very" (almost always cuttable)
- "simply"

## Channel-specific allowlist (we DO use these — don't false-flag)

These phrases overlap with bland writing but match MPD's voice when used
specifically:

- "Here's what's actually happening" — signature reframe phrasing
- "Most people miss this" — pillar P1 hook anchor
- "The pattern reveals" — channel anchor phrase
- "You'd think X, but actually Y" — Pillar P1 setup

## Sentence-opening variety

No more than 2 chapters in a single video may open with the same construction.
Examples of constructions:
- Question lead ("Why do…", "What if…")
- Number lead ("In 2008…", "Forty-three percent of…")
- Subject-verb lead ("Honeyfund built…", "Banks make money…")
- Imperative ("Watch what happens…", "Look at this number…")

## Update protocol

When a slop phrase is observed in a real script during Stage 3.1 or 3.2:
1. User flags via the relevant learning log (30 or 31).
2. During quarterly pattern review, recurring instances (3+ episodes) get
   promoted to Hard Ban here.
3. Bump version + updated frontmatter, push.
