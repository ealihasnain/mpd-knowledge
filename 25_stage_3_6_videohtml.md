---
id: 25_stage_3_6_videohtml
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.6]
---

# Stage 3.6 — Video HTML

## Output

**Filename:** `MPD_D###_TopicShort_VideoHTML_v#.html`
**Workspace path:** `D###_TopicShort\06_VideoHTML_v#.html`
**Format:** Self-contained HTML — embedded CSS, embedded SVG assets, no
external resources (offline-renderable).

This is the visual rendering layer of the episode. Played fullscreen at
1920×1080 with audio overlaid, it becomes the video.

## Inputs

- Strategy Brief (sections: chapters, visual asset prescription)
- Voice Script (chapter timing plan)
- `05_CaptionsWord_v#.srt` — word-level timestamps for iconTimes mapping
- `05_Words_v#.json` — alternative source for word timestamps
- Style tokens (`10_style_tokens.md`)
- Active Rules from 35_learnings_3_6.md

## Required HTML structure

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>MPD D### — [topic] — Video</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@900&family=Barlow:wght@400;700&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
  <style>
    :root {
      --canvas-base: #E4DDD0;
      --ink: #2A2520;
      --accent-primary: #2DB89D;
      --accent-secondary: #F5C518;
      --alert-reveal: #E63946;
      --supporting: #8BA8B5;
      --font-display: "Barlow Condensed", sans-serif;
      --font-body: "Barlow", sans-serif;
      --font-mono: "DM Mono", monospace;
    }
    /* Full chapter card styling, animations, paper grain overlay, etc. */
  </style>
</head>
<body>

<!-- Paper grain overlay (mandatory per 10_style_tokens.md) -->
<div class="grain"></div>

<!-- Chapter cards — one per chapter -->
<section class="chapter" data-chapter="01" data-start="0" data-end="72">
  <div class="chapter-num">CHAPTER 01</div>
  <h1 class="chapter-title">[Title]</h1>
  <div class="chapter-stat">$264 BILLION</div>
  <div class="chapter-context">[short subtitle]</div>
</section>

<!-- Stat slams, pattern interrupts, icon triggers — distributed through timeline -->

<!-- Icon triggers — Section at end -->
<section id="icon-times">
  <h2>Icon Triggers (data-driven)</h2>
  <script type="application/json" id="iconTimes">
    [
      {"t": 1.4,  "type": "chapter-card", "chapter": 1, "duration_ms": 800},
      {"t": 12.7, "type": "stat-slam", "value": "$264B", "duration_ms": 1500},
      {"t": 34.2, "type": "pattern-interrupt", "asset": "warrenBuffett-portrait", "duration_ms": 2400}
      /* one entry per visual beat */
    ]
  </script>
</section>

<!-- NEW ASSETS FOR LIBRARY manifest -->
<section id="new-assets">
  <h2>New Assets for Library</h2>
  <ul>
    <li>portrait_jaysmith_v1.svg — used in Ch 03 pattern interrupt @ 4:23</li>
    <li>brand_vanguard_v1.svg — used in Ch 05 stat slam @ 6:12</li>
  </ul>
  <!-- if no new assets, explicitly note: "No new assets — all visuals reused from corpus library." -->
</section>

</body>
</html>
```

## Critical rules (audited)

### G6 — Icon trigger mapping (binary fail)

Every entry in `iconTimes[]` array's `"t"` field MUST be a real timestamp
where the corresponding concept is spoken. Producer derives these from:

1. The chapter timing plan (Voice Script Section 1) — gives chapter start
   times.
2. The word-level SRT (`05_CaptionsWord_v#.srt`) — gives exact moment a
   specific word is spoken.

For each iconTimes entry, producer:
- Identifies the word in the script that triggers the visual ("Buffett",
  "$264B", "the pattern")
- Finds that word's timestamp in `05_CaptionsWord_v#.srt`
- Uses that timestamp as `"t"` (seconds, decimal, from audio start)

**Phantom triggers** (placeholder times that don't match a real word) =
G6 binary fail.

### G7a — NEW ASSETS manifest (binary fail)

Section `#new-assets` MUST exist. If no new assets were created for this
episode (all visuals reused), the section must explicitly say so:

```html
<section id="new-assets">
  <h2>New Assets for Library</h2>
  <p>No new assets — all visuals reused from corpus library.</p>
</section>
```

Missing section = G7a fail.

### Style token compliance (binary fail)

CSS variables `--canvas-base`, `--ink`, `--accent-primary`,
`--accent-secondary`, `--alert-reveal`, `--supporting` MUST be in `:root`
block. Off-palette colors (not from this list, except for true neutrals
like white/black) = binary fail.

Only fonts: Barlow Condensed 900, Barlow 400/700, DM Mono 400/500.

### Paper grain overlay (binary fail)

Mandatory `body::before` or `.grain` element with mix-blend-mode multiply,
opacity 0.5, fixed positioning. Without it, the channel's signature warm
paper aesthetic is broken.

## Asset prescription discipline

Reuse from corpus library wherever possible. Cross-reference
`06_corpus_index.md` asset library section for available SVGs.

Asset naming convention (from learning log 39):
- `<category>_<short_name>_v#.svg`
- Categories: `portrait`, `country`, `brand`, `icon`, `chartTemplate`,
  `lowerThird`, `transition`
- Short names: PascalCase, ≤12 chars

Examples:
- `portrait_warrenBuffett_v1.svg`
- `brand_amex_v1.svg`
- `country_usa_v1.svg`

## Token budget guidance

This stage is the heaviest. Producer fetches ~7K tokens of refs + needs
Strategy Brief (~15K) + Voice Script (~10K) + word-level SRT (~5K) in
context = ~37K tokens loaded before generation. Generated HTML is typically
20K–35K tokens.

**Mandatory:** open fresh chat for Stage 3.6. First message: paste the
Strategy Brief chapters section + Voice Script chapter timing plan + word-
level SRT. The producer can request specific other sections as needed.

If audit cycle 2 triggers heavy revisions, context can blow. Use
`mpd-handoff` to split mid-revision if approaching 75% context.

## Failure modes to avoid

- **iconTimes timestamps invented.** Producer must reference real word-SRT
  timestamps, not guess.
- **Chapter cards with 5+ words in title.** Read time at fullscreen is
  critical; max 4 words.
- **Animations longer than 500ms for transitions.** Viewer interpret as
  "loading" delay.
- **No paper grain.** Aesthetic-breaking; binary fail.
- **Off-palette colors.** Even one rogue `#FF5733` = binary fail.

## Auto-write on completion

Same protocol: progress.md row 3.6 → passed, 35_learnings_3_6.md Episode
Log line, 3 downloads.
