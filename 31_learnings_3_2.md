---
id: 31_learnings_3_2
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.2]
---

# Learnings — Stage 3.2 (Voiceover Script)

**Auto-read** at stage start (Active Rules → gate input).
**Auto-written** at stage end (one Episode Log line, no user prompt).

## Active Rules

- [SEED] TTS-safe: NO ellipses (… or ...), em-dashes (—), semicolons, parentheses, abbreviations (write "Doctor" not "Dr.", "United States" not "U.S."), numerals in spoken text (write "five hundred" not "500"). Violations = G3 fail.
- [SEED] 4 mandatory emotional variation moments per voiceover: Hook (0:00–0:30, curiosity/disbelief), First Reveal (1:30–2:30, mechanism satisfaction), Stakes Raise (midpoint, "why this matters to you"), Crystallization (final 30s, one-line pattern).
- [SEED] Each scriptbox part hard cap 5,000 characters INCLUDING emotion tags. Vista bills per character; budget like cash.
- [SEED] Last sentence of Part 1 and first sentence of Part 2 must use emotion tags from the SAME family (e.g., both `<thoughtful>` or both `<excited>`). Cross-family seams produce audible voice flips (G3a fail).
- [SEED] Every numeric figure in the voice script must echo a datapoint already present in the Strategy Brief Compact Info payload. Numbers introduced mid-script that don't trace back = G2 fail.
- [SEED] Use contractions naturally ("it's", "you're", "we'll"). Formal robotic prose breaks KateAsta's conversational register.
- [SEED] No sentence > 28 words. Hard cap.
- [SEED] One sentence per line in scriptbox blocks (improves Vista's voice_v3 phrasing).
- [SEED] ElevenLabs emotion tags per sentence: `<excited>`, `<thoughtful>`, `<concerned>`, `<satisfied>`, `<curious>`, `<resolved>`. Match tag to content; do not default to one tag throughout.
- [SEED] Mid-point re-hook (50–60% mark) required: a line like "And here's the part nobody talks about" or "Watch what happens when…".
- [SEED] Pattern interrupt every 90–120 seconds: unexpected analogy, named example, or shift in stakes.

## Episode Log (newest first)

*(No entries yet.)*

## Pending Promotions

*(No pending promotions yet.)*
