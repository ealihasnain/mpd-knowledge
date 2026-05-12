---
id: 27_stage_3_8_thumbnail
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.8]
---

# Stage 3.8 — Thumbnail

## Output

**Filename:** `MPD_D###_TopicShort_Thumbnail_v#.png`
**Workspace path:** `D###_TopicShort\09_Thumbnail_v#.png`
**Specs:** 1280×720 PNG, sRGB, < 2MB, contrast ratio ≥ 7:1

## Producer's role

Generate the thumbnail as an HTML file that the user renders to PNG via
their browser's "save as image" or screenshot. (Future v1.4: SVG direct
export.)

## Output: HTML file that renders to thumbnail

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>MPD D### Thumbnail v#</title>
  <style>
    :root {
      --canvas-base: #E4DDD0;
      --ink: #2A2520;
      --accent-primary: #2DB89D;
      --accent-secondary: #F5C518;
      --alert-reveal: #E63946;
      --supporting: #8BA8B5;
    }
    body {
      margin: 0;
      width: 1280px;
      height: 720px;
      background: var(--canvas-base);
      font-family: "Barlow Condensed", sans-serif;
      overflow: hidden;
      position: relative;
    }
    .grain {
      position: absolute;
      inset: 0;
      /* same SVG noise as in 10_style_tokens.md */
      mix-blend-mode: multiply;
      opacity: 0.5;
      pointer-events: none;
    }
    .number {
      position: absolute;
      left: 80px;
      top: 220px;
      font-family: "Barlow Condensed", sans-serif;
      font-weight: 900;
      font-size: 280px;
      color: var(--accent-secondary);
      letter-spacing: -0.04em;
      line-height: 0.85;
    }
    .title {
      position: absolute;
      left: 80px;
      bottom: 80px;
      font-family: "Barlow Condensed", sans-serif;
      font-weight: 900;
      font-size: 108px;
      color: var(--ink);
      line-height: 0.95;
      max-width: 900px;
    }
    .icon {
      position: absolute;
      right: 80px;
      top: 80px;
      width: 280px;
      height: 280px;
    }
    /* OR a face image — never both */
  </style>
</head>
<body>
  <div class="grain"></div>
  <div class="number">$264B</div>     <!-- amber dollar amount — channel signature -->
  <div class="title">YOUR TAX REFUND IS A LOAN</div>  <!-- ≤5 words, all caps -->
  <svg class="icon" viewBox="0 0 200 200">
    <!-- one stylized icon, no face if icon present -->
    <!-- OR replace with <img class="icon" src="data:image/jpeg;base64,..."/> for face — never both -->
  </svg>
</body>
</html>
```

## Critical rules

| Rule | Threshold | Type |
|---|---|---|
| Format | 1280×720 PNG | Binary |
| File size | < 2 MB | Binary |
| Title word count | ≤ 5 words | Binary |
| Title font size | ≥ 96px (target 108px) | Binary |
| Contrast (title vs background) | ≥ 7:1 | Binary |
| Faces | Maximum 1 | Binary |
| Icons | Maximum 1 | Binary |
| Face + icon | NEVER both | Binary |
| Amber accent | Required for the dollar/number | Score |
| Mobile readability test | Title legible at 120×68px scale | Score |

## Title formula

`[STRONG VERB] [SUBJECT] [TWIST/IRONY]` — 3 to 5 words.

Examples (good):
- "YOUR TAX REFUND IS A LOAN" (5 words, ironic, concrete)
- "CREDIT CARDS PAY YOUR REWARDS" (5 words, reframe)
- "WHY VANGUARD WANTS LAZY CLIENTS" (5 words, surprise)

Examples (bad):
- "THE SHOCKING TRUTH ABOUT TAX REFUNDS THAT NOBODY KNOWS" (clickbait, >5 words)
- "TAX REFUNDS" (boring, too generic)
- "5 THINGS ABOUT TAX REFUNDS YOU NEED TO KNOW" (listicle vibe, channel mission ban)

## User-side step after producer emits HTML

```
1. Save the thumbnail HTML to D###_TopicShort\
2. Open in Chrome at 1280×720 window size (DevTools > device toolbar > set 1280×720)
3. Right-click > Capture screenshot (or use the Save Full Page Screenshot extension)
4. Save as 09_Thumbnail_v1.png
5. Verify file size with: dir 09_Thumbnail_v1.png (should be <2MB)
6. Reply: "thumbnail saved, NN KB, contrast verified"
```

(Manual contrast check: paste title hex + background hex into webaim.org/resources/contrastchecker/)

## Auto-write on completion

Same: progress.md → 3.8 passed, 37_learnings_3_8.md log line, 3 downloads.
