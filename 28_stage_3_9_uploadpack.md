---
id: 28_stage_3_9_uploadpack
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.9]
---

# Stage 3.9 — Upload Pack

## Output

**Filename:** `MPD_D###_TopicShort_UploadPack_v#.html`
**Workspace path:** `D###_TopicShort\10_UploadPack_v#.html`

Single HTML document with 7 sections, each copy-pasteable into YouTube
Studio.

## Required structure

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>MPD D### Upload Pack v#</title>
  <style>/* style tokens for readability — this is for you, not for YouTube */</style>
</head>
<body>

<section class="block">
  <h2>1. TITLE</h2>
  <p class="meta">Limit: 70 chars · Actual: NN</p>
  <div class="copy-target" id="copy-title">[Title text]</div>
</section>

<section class="block">
  <h2>2. DESCRIPTION</h2>
  <p class="meta">Limit: 5,000 chars · Actual: NNNN</p>
  <div class="copy-target" id="copy-desc">
    [Paragraph 1: hook + summary, 2–3 sentences]

    [Paragraph 2: what they'll learn, 3–4 sentences]

    [Paragraph 3: CTA + chapter timestamps]

    Chapters:
    00:00 [Chapter 01 title]
    01:12 [Chapter 02 title]
    02:18 [Chapter 03 title]
    ...

    Subscribe for weekly pattern decodes: @moneypatternsdecoded

    Sources mentioned in this video:
    - [Source 1]
    - [Source 2]
    ...
  </div>
</section>

<section class="block">
  <h2>3. TAGS</h2>
  <p class="meta">Limit: 500 chars total · Actual: NNN · Count: NN tags</p>
  <div class="copy-target" id="copy-tags">tax refund, tax planning, hidden tax cost, IRS, free loan to government, personal finance, money patterns, behavioral economics, financial mistakes, tax season 2026</div>
</section>

<section class="block">
  <h2>4. THUMBNAIL</h2>
  <p>File: <code>09_Thumbnail_v#.png</code> in D###_TopicShort\</p>
  <p>(Upload manually in Studio — this section is just a reference.)</p>
</section>

<section class="block">
  <h2>5. END SCREEN PLAN</h2>
  <p class="meta">Last 20 seconds of video</p>
  <ul>
    <li><strong>0:00–0:08:</strong> Subscribe element (right-side circle)</li>
    <li><strong>0:08–0:18:</strong> Related video card (related pillar, e.g., D### for P1)</li>
    <li><strong>0:00–0:20:</strong> Channel watermark (bottom-left)</li>
  </ul>
</section>

<section class="block">
  <h2>6. PINNED COMMENT</h2>
  <p class="meta">Limit: 1,500 chars · Actual: NNN</p>
  <div class="copy-target" id="copy-pinned">[Pinned comment text — includes the Open Loop payoff. Example: "If you spotted the $264 callback — that's the pattern. Most don't see it because [reason]. Curious which pattern you'd want decoded next? Drop a topic below."]</div>
</section>

<section class="block">
  <h2>7. COMMUNITY POST</h2>
  <p class="meta">Limit: 5,000 chars · Actual: NNN · Type: question</p>
  <div class="copy-target" id="copy-community">[Question-based post that drives engagement. Example: "Quick check before tomorrow's drop: do you know what your bank earns on your checking balance while it sits there? Comment your guess. The actual number is wilder than most think — and it's the basis of how 'free' checking accounts make money. Video drops [day]."]</div>
</section>

</body>
</html>
```

## Critical rules

| Section | Limit | Type |
|---|---|---|
| Title | ≤ 70 chars | Binary |
| Description | ≤ 5,000 chars | Binary |
| Tags | ≤ 500 chars total, 10–15 individual | Binary |
| Pinned comment | ≤ 1,500 chars | Binary |
| Community post | ≤ 5,000 chars | Binary |
| End screen | 3 elements, ≤ 20s | Binary |

All 7 sections present = G10 pass.

## Title formula (reuse from 3.8 if appropriate)

Often the thumbnail title and video title are the same or very close. They
can differ if needed for SEO vs visual impact, but consistency helps CTR.

## Description structure

Paragraph 1 (hook + summary): 2–3 sentences. Open with the reframe.
Paragraph 2 (what they'll learn): 3–4 sentences. Specific takeaways.
Paragraph 3 (CTA + chapters): Subscribe nudge + chapter timestamps.

Then: sources list, then channel branding.

Avoid: emojis, ALL CAPS in body, exclamation marks in body, "smash like
button" phrasing, "WAIT TILL YOU SEE" clickbait.

## Tags strategy

First tag: primary SEO keyword from queue.yml (`keyword` field).
Tags 2–5: tight variations.
Tags 6–10: broader category terms.
Tags 11–15 (optional): cross-topic relevance (other pillars).

Don't pad with generic terms ("money", "finance") — they dilute relevance.

## Pinned comment formula

`[Open Loop payoff reference] + [insight] + [engagement question]`

Example: "If you spotted the $264 callback — that's the pattern. Most miss
it because we're trained to think tax refunds are a windfall. Curious which
'free money' you've been giving away? Drop your guesses below."

## Community post type

Question. Always question. Drives comments, which drives algorithmic boost.

Don't: announcement post, link drop, image-only post.

## Auto-write on completion

3.9 → passed, 38_learnings_3_9.md log line, 3 downloads.
