---
id: 20_stage_3_1_strategy
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.1]
---

# Stage 3.1 — Strategy Brief

## Output

**Filename:** `MPD_D###_TopicShort_StrategyBrief_v#.html`
**Format:** Single HTML file, self-contained (no external CSS/JS)
**Workspace path:** `D###_TopicShort\01_StrategyBrief_v#.html`
**Target size:** 800–1,200 lines of HTML (depends on chapter count)

## Inputs

From `queue.yml` (or `1_1c_calendar.yml` if not in queue):
- `topic` — full topic title
- `topic_short` — PascalCase ≤16 chars
- `pillar` — P1, P2, P3, P4, or P5
- `keyword` — primary SEO keyword
- `source_notes` — optional path to research notes

From atomic refs (auto-loaded):
- Voice canon, gates, slop rules, critique checklist, corpus index, Active Rules

## Required HTML structure

The Strategy Brief is the source of truth for the entire episode. Every
downstream stage reads from it. Structure is fixed:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>MPD D### — [topic] — Strategy Brief v#</title>
  <style>
    /* paste full style token block from 10_style_tokens.md */
  </style>
</head>
<body>

<!-- SECTION 1: METADATA HEADER -->
<header class="meta">
  <div class="meta-row">D### · v# · YYYY-MM-DD</div>
  <h1>[Topic]</h1>
  <div class="meta-row">Pillar: P# — [pillar name]</div>
  <div class="meta-row">Keyword: [keyword]</div>
  <div class="meta-row">Target publish: [date or "ship-when-ready"]</div>
</header>

<!-- SECTION 2: RULE 0 ALIGNMENT (from 12_rule_0_criteria.md) -->
<section id="alignment">
  <h2>Rule 0 — Topic Alignment</h2>
  <table>
    <tr><th>Criterion</th><th>Score</th><th>Note</th></tr>
    <tr><td>C1 Hidden pattern</td><td>1</td><td>[note]</td></tr>
    <tr><td>C2 Reframe moment</td><td>1</td><td>[note]</td></tr>
    <tr><td>C3 Depth</td><td>1</td><td>[note]</td></tr>
    <tr><td>C4 No advice angle</td><td>1</td><td>[note]</td></tr>
  </table>
  <p class="rule0-result">SCORE: 4/4 — PROCEED</p>
</section>

<!-- SECTION 3: EXECUTIVE SUMMARY -->
<section id="summary">
  <h2>Executive Summary</h2>
  <p>[3–5 sentence summary of the video's core argument and reveal]</p>
  <div class="callout">
    <strong>The Reframe:</strong> You'd think [conventional view], but
    actually [actual mechanism] because [why].
  </div>
</section>

<!-- SECTION 4: RETENTION ENGINEERING PLAN -->
<section id="retention">
  <h2>Retention Engineering</h2>
  <dl>
    <dt>Open Loop Hook (0:00–0:30):</dt>
    <dd>[the question/disbelief planted in first 30s]</dd>

    <dt>Callback Number:</dt>
    <dd>[specific $ or % introduced in Ch 1, paid off in final chapter]</dd>

    <dt>Pattern Interrupts (every 90–120s):</dt>
    <dd>
      <ul>
        <li>Ch ~2: [analogy / named example / stakes shift]</li>
        <li>Ch ~4: [analogy / named example / stakes shift]</li>
        <li>Ch ~6: [analogy / named example / stakes shift]</li>
      </ul>
    </dd>

    <dt>4 Emotional Variation Moments:</dt>
    <dd>
      <ul>
        <li>Hook (~0:30) — curiosity/disbelief</li>
        <li>First Reveal (~2:00) — mechanism satisfaction</li>
        <li>Stakes Raise (~5:00) — "and here's why this matters to you"</li>
        <li>Crystallization (~final 30s) — the one-line pattern</li>
      </ul>
    </dd>

    <dt>Hidden-Pattern Reveal:</dt>
    <dd>Appears in first 90 seconds (not last quarter). Specifically at: [timestamp]</dd>
  </dl>
</section>

<!-- SECTION 5: AUDIENCE FIT -->
<section id="audience">
  <h2>Audience Pillar Fit</h2>
  <p><strong>Primary (60%) — Curious Professional:</strong> [how this serves them]</p>
  <p><strong>Secondary (30%) — Ambitious Learner:</strong> [how this serves them]</p>
  <p><strong>Tertiary (10%) — Experienced Skeptic:</strong> [how this serves them]</p>
</section>

<!-- SECTION 6: CHAPTER OUTLINE -->
<!-- 7 chapters default, 9 max only if data density justifies -->
<section id="chapters">
  <h2>Chapter Outline</h2>

  <div class="chapter" data-chapter="01">
    <h3>Ch 01 · [Chapter title]</h3>
    <div class="chapter-meta">Target: ~120s spoken · ~180 words · Opener type: [Q/N/SV/IM/AN]</div>
    <p class="chapter-thesis"><strong>Thesis:</strong> [one-sentence chapter purpose]</p>
    <div class="datapoints">
      <table>
        <tr><th>#</th><th>Tag</th><th>Datapoint</th><th>Source</th><th>Use</th></tr>
        <tr><td>D01.01</td><td>VER</td><td>[specific fact]</td><td>[URL or pub+year]</td><td>[where in chapter]</td></tr>
        <tr><td>D01.02</td><td>EST</td><td>[estimate]</td><td>[methodology]</td><td>[where]</td></tr>
        <tr><td>D01.03</td><td>ATT</td><td>[attributed claim]</td><td>[who said it]</td><td>[where]</td></tr>
      </table>
    </div>
    <div class="visual-prescription">
      <strong>Visual:</strong> [chapter card title / icon / pattern interrupt]
    </div>
  </div>

  <!-- repeat for Ch 02 through Ch 07 -->

</section>

<!-- SECTION 7: COMPACT INFO PAYLOAD (FOR DOWNSTREAM 3.2) -->
<section id="compact-info">
  <h2>Compact Info Payload (for Stage 3.2)</h2>
  <p><em>Stage 3.2 must echo every number listed here. G2 enforces.</em></p>
  <pre><code>{
  "episode": "D###",
  "topic_short": "[TopicShort]",
  "pillar": "P#",
  "callback_number": "[the specific $ or % to plant in Ch 1 + payoff in final]",
  "chapter_word_targets": {
    "01": 180, "02": 165, "03": 175, "04": 150, "05": 180, "06": 160, "07": 140
  },
  "datapoints_to_echo": [
    {"tag": "VER", "value": "$264", "chapter": 1, "use": "opening hook"},
    {"tag": "VER", "value": "43%", "chapter": 2, "use": "reframe"},
    {"tag": "EST", "value": "$12 billion", "chapter": 4, "use": "stakes raise"}
    /* ≥80 entries total across all chapters */
  ],
  "open_loop": "[the question planted in first 30s]",
  "open_loop_payoff_chapter": 7,
  "reframe_pivot_chapter": 3,
  "hidden_pattern_timestamp_seconds": 75
}</code></pre>
</section>

<!-- SECTION 8: ASSET PRESCRIPTION -->
<section id="assets">
  <h2>Visual Asset Prescription</h2>
  <p>For each chapter, the visual element required:</p>
  <table>
    <tr><th>Chapter</th><th>Asset type</th><th>Reuse from library?</th><th>New asset needed?</th></tr>
    <tr><td>01</td><td>Chapter card + dollar-number callout</td><td>chapter-card template</td><td>Dollar-figure styling</td></tr>
    <!-- one row per chapter -->
  </table>
</section>

<!-- SECTION 9: SOURCES INDEX -->
<section id="sources">
  <h2>Sources Index</h2>
  <ol>
    <li>[URL or citation 1]</li>
    <li>[URL or citation 2]</li>
    <!-- one per unique source across all VER and ATT datapoints -->
  </ol>
</section>

</body>
</html>
```

## Critical requirements (audited)

| Gate | Threshold |
|---|---|
| G1 datapoint count | ≥ 80 total across all chapters (binary fail) |
| G1 source attribution | Every datapoint has VER/EST/ATT tag + source field (binary fail) |
| G12 slop check | All criteria per 09_gate_G12_slop.md |
| Retention rules | All 11 Active Rules in 30_learnings_3_1.md must pass |
| Pillar word target | Total word target per pillar:<br>P1: 1,150–1,300 · P2: 1,300–1,450 · P3: 1,150–1,300 · P4: 1,350–1,500 · P5: 1,000–1,150 |
| Chapter count | 7 default, 9 max if data density justifies |
| Compact Info | Section 7 must be present and parseable JSON |

## Datapoint tagging

| Tag | Meaning | Use case |
|---|---|---|
| **VER** | Verified — published with named source | "$264 billion lost to lottery winners (FRBNY 2019)" |
| **EST** | Estimate — your derivation with shown methodology | "~$12B/year industry (est. from market sizing × take rate)" |
| **ATT** | Attributed — claim by named person/org, even if unverified | "Buffett: 'never invest in what you don't understand' (Berkshire AGM 2008)" |

## Failure modes to avoid

- **Padding chapters with restatement.** If Ch 4 says "and here's another example" without a new mechanism, cut it. Better 6 dense chapters than 9 with two padding ones.
- **Generic stats.** "Many people struggle with saving" is not a datapoint. "Vanguard's 2024 How America Saves report shows 32% of 401k participants contribute below their employer match threshold" is.
- **Reframe placed in final chapter.** It must land by Ch 3 (mid-video) — otherwise viewers don't see the payoff in the AVD-critical zone.
- **Open Loop without explicit payoff plan.** Compact Info must specify which chapter pays it off.

## Token budget guidance

This stage is context-heavy. Producer fetches ~6K tokens of atomic refs + Active Rules. Generated brief is typically 12K–18K tokens of HTML. Audit cycles add 30–50% overhead. Stay under 50% of chat context; trigger mpd-handoff if approaching.

## Auto-write on completion

After audit emission:
1. Update progress.md row 3.1 → `passed` (or `soft_passed`).
2. Update 30_learnings_3_1.md Episode Log with one line.
3. Emit 3 downloads: brief HTML, updated learning log, updated progress.md.
