---
id: 10_style_tokens
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.6, 3.8]
---

# Style Tokens — Production Palette

**Non-negotiable.** Used in Stage 3.6 (Video HTML) and Stage 3.8 (Thumbnail).
Any deviation = binary fail in those stages' gate checks.

## Color palette

| Token | Hex | Usage |
|---|---|---|
| `--canvas-base` | `#E4DDD0` | HTML background — warm parchment paper. Never change. Apply grain overlay at 50% multiply. |
| `--ink` | `#2A2520` | Primary text and structural elements. Warm dark, not pure black. |
| `--accent-primary` | `#2DB89D` | Teal — active states, chapter markers, key highlights, CTAs. |
| `--accent-secondary` | `#F5C518` | Amber — stat slams, data points, "aha" moments, emphasis numbers. |
| `--alert-reveal` | `#E63946` | Red — shocking stats, negative comparisons, the cost being revealed. |
| `--supporting` | `#8BA8B5` | Slate — labels, subtext, secondary data. Never dominant. |

## CSS variable block (paste into every Stage 3.6 HTML)

```css
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
```

## Typography — three fonts only

| Font | Weights | Usage |
|---|---|---|
| **Barlow Condensed** | 900 | All headlines, stat slams, chapter titles, thumbnails. Tight letter-spacing for max visual impact. |
| **Barlow** | 400, 700 | Body text, labels, mid-weight explanations. |
| **DM Mono** | 400, 500 | Data, codes, metadata, monospaced UI elements, source citations. |

Google Fonts import:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@900&family=Barlow:wght@400;700&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
```

## Background grain texture

Every Stage 3.6 HTML body must include a CSS-generated paper grain overlay:

```css
body::before {
  content: "";
  position: fixed;
  inset: 0;
  pointer-events: none;
  background-image: url('data:image/svg+xml,...');  /* 1px noise SVG */
  mix-blend-mode: multiply;
  opacity: 0.5;
  z-index: 1;
}
```

Reference noise SVG: 200×200 px stippled noise, included in the
chapter_card_template.html (Phase 4 build).

## Thumbnail rules (Stage 3.8)

- 1280×720 PNG
- Heavy use of `--accent-secondary` (amber) for the dollar/number
- One face or one icon — never both
- Title text: Barlow Condensed 900, max 5 words, font size ≥ 96px
- Contrast ratio ≥ 7:1 between title and background
