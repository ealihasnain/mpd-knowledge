---
id: 11_critique_checklist_global
version: 1.0
updated: 2026-05-10
applies_to_stages: [all]
---

# Global Critique Checklist

Cross-stage rules applied during every stage's self-critique loop, in
addition to stage-specific gates.

## The self-critique loop

```
PRODUCE output
EVALUATE against [stage gates + Active Rules from learning log + this checklist]
  Score each criterion 1–10 OR pass/fail
IF any criterion < 8 OR any binary fail:
  REVISE targeting failed criterion(a)
  RE-EVALUATE
  REPEAT (max 3 cycles)
IF cycle 3 reached AND criteria still failing:
  EMIT output
  FLAG unresolved criteria in critique_history.md
  CONTINUE to next stage
ELSE:
  EMIT output silently
```

## Universal rules (every stage)

| # | Rule | Type |
|---|---|---|
| U1 | No financial advice phrasing ("you should buy", "invest in", "I recommend") | Binary fail |
| U2 | No fearmongering or conspiracy framing ("they don't want you to know", "the system is rigged") | Binary fail |
| U3 | No clickbait phrasing in titles, hooks, or thumbnails | Binary fail |
| U4 | No reference to courses, products, sponsors, upsells | Binary fail |
| U5 | Pillar consistency — output must reflect the assigned pillar (P1–P5) framing | Score ≥ 8 |
| U6 | Audience-trait alignment — written for the curious professional, not the day-trader or the academic | Score ≥ 8 |

## Quality dimensions (where applicable)

| Dimension | Scored at stages | Notes |
|---|---|---|
| Hook strength | 3.1, 3.2, 3.6, 3.9 | First 30s curiosity gap. Score 1–10. |
| Reframe clarity | 3.1, 3.2 | "Most people think X, but actually Y because Z." |
| Mechanism explanation | 3.1, 3.2 | The how/why behind the pattern. |
| Concrete-fact density | 3.1, 3.2, 3.6 | ≥ 3 named entities or specific numbers per chapter (G12 criterion). |
| Retention engineering | 3.1, 3.2 | Open Loop Hook + Callback Number + mid-point re-hook + 4 emotional shifts. |
| Visual asset fit | 3.6, 3.8 | Asset prescription supports the spoken content. |

## Anti-padding test

Every example, statistic, or anecdote in a stage 3.1 brief or 3.2 script
must earn its place. Per-chapter rule:

- 1st example: required
- 2nd example: optional, only if it adds a distinct angle
- 3rd example: rare; only if it lands a payoff that the 1st and 2nd haven't

Critique question: "If I removed example #N, what would the chapter lose?"
If the answer is "nothing material" → cut it.

## Soft-fail logging format

When max 3 revision cycles complete and gates still fail, append to
`critique_history.md`:

```
[YYYY-MM-DD HH:MM PKT] Stage 3.X — SOFT FAIL
  Failed criteria: G2 (data echo, 1 number unmatched), G12 criterion 4 (chapter opener variety)
  Revision attempts: 3
  Decision: emitted v3, continuing pipeline
  Notes: <optional one-line context>
```

## Hard halts (rare; never auto-recover in chat-only mode)

If any of these occur, stop, write a clear explanation to chat, and exit:

- Source data unavailable (no Strategy Brief = no Voice Script possible)
- File path inaccessible (workspace folder missing)
- Companion tool URL returns 404 (browser tool offline)

User intervenes manually.
