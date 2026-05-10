---
id: 04_voice_canon
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.1, 3.2, 3.6, 3.8, 3.9]
---

# Voice Canon — KateAsta + Brand Tone

## TTS settings (locked)

Provider: **vistatts.com** (ElevenLabs reseller). Internally Vista wraps
ElevenLabs — voice ID, model name, and ElevenLabs-style settings pass
through unchanged; Vista adds a `speed` parameter on top.

| Field | Value |
|---|---|
| `voice_id` | `UbWKKaYfYWMB1x0WtvN7` (KateAsta) |
| `voice_name` | `KateAsta` |
| `model_id` | `eleven_v3` |
| `stability` | `0.52` (target 0.50–0.55 range) |
| `similarity_boost` | `0.78` (target 0.75–0.80) |
| `style` | `0.12` (target 0.10–0.15) |
| `speed` | `1.0` (Vista-specific, default) |
| `use_speaker_boost` | `true` |
| `output_format` | `mp3_44100_192` (44.1 kHz, 192 kbps) |

## Tone — how we sound

✓ **Sound like:**
- "Here's what's actually happening behind the scenes…"
- "Most people miss this, but…"
- "The pattern reveals something important…"
- "You'd think X, but actually Y because…"
- "Watch what happens when…"

✗ **Never sound like:**
- "You NEED to know this!" (fearmongering)
- "They don't want you to know…" (conspiracy)
- "Smash that like button!" (desperate)
- "This one weird trick…" (clickbait)
- "As I mentioned in my course…" (selling)

See [05_voice_blocklist.md](05_voice_blocklist.md) for the explicit anti-slop
banned-phrase list.

## Sentence rhythm rules

- No sentence > 28 words.
- Max 2 same-length sentences in a row (mix short, medium, long).
- Avoid passive constructions where active works.
- Use contractions naturally ("it's", "you're", "we'll") — formal robotic
  prose breaks the conversational register KateAsta delivers best.
- Numbers: spell out under 10 in voiceover scripts (TTS-safe); use numerals
  in HTML strategy briefs and on-screen text.

## TTS-safe rules (Stage 3.2 voiceover scripts)

- No ellipses (`…` or `...`)
- No em-dashes (`—`) — use commas or full stops
- No semicolons
- No parentheses
- No numerals in spoken text (write "five hundred", not "500")
- No abbreviations (write "Doctor", not "Dr."; "United States", not "U.S.")
- One sentence per line in scriptbox blocks (helps Vista's voice_v3 phrasing)

## Emotional variation moments (mandatory in every voiceover)

Every Stage 3.2 voice script must contain 4 distinct emotional shifts:

1. **Hook moment** — ~0:00–0:30, builds curiosity/disbelief
2. **First reveal** — ~1:30–2:30, satisfies the hook with mechanism
3. **Stakes raise** — ~midpoint, "and here's why this matters to you"
4. **Crystallization** — ~final 30s, the one-line pattern they'll remember

Use ElevenLabs emotion tags (`<excited>`, `<thoughtful>`, `<concerned>`,
`<satisfied>`, etc.) per sentence as appropriate.

## Phrases for retention

- Open Loop Hook: posed in first 30s, paid off in last 60s
- Callback Number: a specific dollar/percentage figure introduced in chapter 1
  and re-referenced in the final chapter
- Mid-point re-hook (50–60% mark): "And here's the part nobody talks about…"
- Pattern interrupt (every 90–120s): unexpected analogy, named example, or
  shift in stakes
