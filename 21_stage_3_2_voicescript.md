---
id: 21_stage_3_2_voicescript
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.2]
---

# Stage 3.2 — Voiceover Script

## Output

**Filename:** `MPD_D###_TopicShort_VoiceScript_v#.html`
**Format:** HTML with two `<scriptbox>` blocks (one per TTS render part)
**Workspace path:** `D###_TopicShort\02_VoiceScript_v#.html`

## Inputs

- `01_StrategyBrief_v#.html` from prior stage — read the Compact Info payload (Section 7)
- Atomic refs auto-loaded: naming, voice canon, voice blocklist, gates, slop check, critique checklist, Active Rules

## Required HTML structure

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>MPD D### — [topic] — Voice Script v#</title>
  <style>/* style tokens */</style>
</head>
<body>

<header>
  <div class="meta-row">D### · v# · YYYY-MM-DD</div>
  <h1>[Topic] — Voice Script</h1>
</header>

<section id="chapter-table">
  <h2>Chapter Timing Plan</h2>
  <table>
    <tr><th>Ch</th><th>Title</th><th>Words</th><th>Target sec</th><th>Cumul</th><th>Part</th></tr>
    <tr><td>01</td><td>[title]</td><td>180</td><td>72</td><td>0:00–1:12</td><td>1</td></tr>
    <tr><td>02</td><td>[title]</td><td>165</td><td>66</td><td>1:12–2:18</td><td>1</td></tr>
    <!-- continue for all chapters -->
  </table>
  <p>Split point: end of Ch [N] (Part 1 ends with <code>&lt;satisfied&gt;</code>, Part 2 begins with <code>&lt;satisfied&gt;</code>).</p>
</section>

<section id="scriptbox-1">
  <h2>Scriptbox · Part 1</h2>
  <p class="meta">Character count: NNNN / 5000 max · Emotion tags: NN</p>
  <pre class="script">[full Part 1 text — one sentence per line, emotion tag per sentence, no ellipses/em-dashes/numerals/abbreviations/parens/semicolons]

&lt;curious&gt;Here's something most people miss.
&lt;curious&gt;Last year, Americans gave the government a free loan of two hundred sixty four billion dollars.
&lt;thoughtful&gt;And they thanked the IRS for the privilege.
...

&lt;satisfied&gt;That's the kind of pattern hidden in plain sight.</pre>
</section>

<section id="scriptbox-2">
  <h2>Scriptbox · Part 2</h2>
  <p class="meta">Character count: NNNN / 5000 max · Emotion tags: NN</p>
  <pre class="script">&lt;satisfied&gt;[opens with same emotion family as Part 1 close]
&lt;thoughtful&gt;...
...
&lt;resolved&gt;That two hundred sixty four billion isn't an accident. It's the pattern.</pre>
</section>

<section id="emotional-checks">
  <h2>4 Emotional Variation Moments — verification</h2>
  <ul>
    <li>Hook (0:00–0:30): Line ___, emotion tag &lt;curious&gt; / &lt;disbelief&gt;</li>
    <li>First Reveal (~2:00): Line ___, emotion tag &lt;satisfied&gt; / &lt;thoughtful&gt;</li>
    <li>Stakes Raise (~50% mark): Line ___, emotion tag &lt;concerned&gt; / &lt;stakes&gt;</li>
    <li>Crystallization (final 30s): Line ___, emotion tag &lt;resolved&gt; / &lt;clarity&gt;</li>
  </ul>
</section>

<section id="data-echo-check">
  <h2>G2 Data Echo Verification</h2>
  <p>Every numeric figure in Part 1 + Part 2 traces to Compact Info datapoints:</p>
  <table>
    <tr><th>Number in script</th><th>Compact Info datapoint ID</th><th>Match</th></tr>
    <tr><td>two hundred sixty four billion</td><td>D01.01 ($264B)</td><td>✓</td></tr>
    <!-- one row per numeric reference -->
  </table>
</section>

</body>
</html>
```

## Critical rules

### TTS-safe writing (binary fails)

In `<pre class="script">` blocks, the following are PROHIBITED:

| Prohibited | Reason | Fix |
|---|---|---|
| `…` or `...` | TTS reads as "dot dot dot" | Replace with sentence break |
| `—` (em-dash) | TTS reads as "minus" or skips | Replace with comma or full stop |
| `;` semicolon | TTS pauses awkwardly | Split into two sentences |
| `(parens)` | TTS reads or muddles | Restructure sentence |
| numerals | TTS may stumble; pronunciation inconsistent | Spell out: "five hundred" not "500" |
| Abbrev (Dr., U.S.) | TTS reads as letters | Spell out: "Doctor", "United States" |
| Sentences > 28 words | KateAsta cadence breaks | Split |
| Multiple sentences per line | Vista v3 phrasing breaks | One sentence per line |

### Emotion tags per sentence

Every sentence must have a leading emotion tag. Vista's `eleven_v3` model uses these:

| Tag | Use |
|---|---|
| `<curious>` | Hook setup, "watch what happens", investigative opens |
| `<thoughtful>` | Mechanism explanations, mid-chapter pivots |
| `<satisfied>` | First reveal, pattern recognition moments |
| `<concerned>` | Stakes raises, "and here's why this matters" |
| `<resolved>` | Crystallization, final-chapter clarity |
| `<excited>` | Use sparingly — only for genuine "aha" beats |
| `<disbelief>` | Hook moments where the reveal is counterintuitive |

Default to `<thoughtful>` if uncertain; flag for review if more than 60% of script uses one tag.

### Seam continuity (G3a)

Last sentence of Part 1 and first sentence of Part 2 must use emotion tags
from the **same family** (per voice canon §"Production Palette"):

| Family | Tags |
|---|---|
| Curious | `<curious>`, `<disbelief>` |
| Reflective | `<thoughtful>`, `<satisfied>` |
| High-stakes | `<concerned>`, `<excited>` |
| Resolved | `<resolved>` |

Cross-family seam = G3a binary fail.

### Character budget (G3)

Each scriptbox: ≤ 5,000 characters INCLUDING emotion tags. Vista bills per
character. Track during writing, not at end.

Typical: ~3,500 chars per part for an 8-minute video (~2,000 spoken words
across both parts).

### Data echo (G2)

Every numeric phrase in either scriptbox traces to a Compact Info datapoint
(see Section 7 of Strategy Brief). The verification table (Section 5 of
Voice Script) makes this explicit. Missing entries = G2 fail.

Numbers in spoken text are spelled out ("two hundred sixty four billion")
but the table column "Number in script" can show the digit form for
clarity ("$264B").

## Pre-script structural pass

Before writing any lines, producer:
1. Reads Strategy Brief Compact Info.
2. Builds the Chapter Timing Plan (Section 1) — totals = pillar word target ± 5%.
3. Decides split point (end of which chapter Part 1 ends at).
4. Then writes the scriptboxes in order, sentence-by-sentence with tags.

Skipping the timing-plan step leads to imbalanced parts; one will overflow 5000 chars.

## Failure modes to avoid

- **All chapters in Part 1.** Splits should target ~50/50 word balance.
- **Heavy emotion-tag concentration.** If 80% of sentences are `<thoughtful>`, the voice sounds monotone. Mix.
- **Sentences with 3+ proper nouns in a row.** TTS will rush them. Break or simplify.
- **Hook delayed past line 5 of Part 1.** Curiosity must hit in first 3 sentences.
- **Crystallization missed.** Final 2–3 sentences of Part 2 must restate the pattern in one tight line.

## Token budget guidance

Stage 3.2 typically fetches ~5K tokens of refs + Active Rules + the full
Strategy Brief from prior stage (~15K tokens loaded as context). Generated
script is ~10K tokens. Audit cycles add ~30%. Risk of context pressure if
Strategy Brief is loaded inline.

**Recommendation:** open fresh chat for Stage 3.2. First message: paste the
Compact Info payload (Section 7 only, ~2K tokens) rather than the full
brief. Producer can request the full brief if a specific section is needed.

## Auto-write on completion

Same protocol as 3.1: progress.md row update, learning log Episode Log line,
3 downloads emitted.
