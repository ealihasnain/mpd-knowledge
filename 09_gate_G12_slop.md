---
id: 09_gate_G12_slop
version: 0.1
updated: 2026-05-10
applies_to_stages: [3.1, 3.2, 3.6, 3.8, 3.9]
---

# Gate G12 — Anti-Slop Check

**Status:** Phase 5 build — initial seed. Refine after D003.

Runs after every text-generating stage (3.1, 3.2, 3.6, 3.8, 3.9).

## Criteria

| # | Criterion | Type | Threshold |
|---|---|---|---|
| 1 | Blocked-phrase count | Binary | = 0 |
| 2 | Concrete-fact density | Binary | ≥ 3 named entities or specific numbers per chapter |
| 3 | Sentence-rhythm variety | Score 1–10 | ≥ 7 |
| 4 | Chapter-opener variety | Binary | No two chapters open with the same construction |
| 5 | Voice fingerprint match | Score 1–10 | ≥ 7 (vs KateAsta canon in 04_voice_canon.md) |

## Implementation

### Criterion 1 — Blocked-phrase count

Producer fetches [05_voice_blocklist.md](05_voice_blocklist.md), extracts
the Hard Ban list, runs case-insensitive substring match against the stage
output. Any hit = binary fail.

### Criterion 2 — Concrete-fact density

For each chapter, count:
- Named entities (proper nouns: company names, person names, country names)
- Specific numbers (dollar amounts, percentages, dates, quantities — not
  vague references like "many" or "most")

Threshold: ≥ 3 per chapter. Less than 3 = binary fail.

### Criterion 3 — Sentence-rhythm variety

Sliding window of 4 consecutive sentences. Compute word-count standard
deviation. Score:

- σ ≥ 8 → 10/10
- σ 6–8 → 8/10
- σ 4–6 → 6/10
- σ 2–4 → 4/10
- σ < 2 → 2/10

Any window scoring < 7 reduces the stage criterion to that score.

### Criterion 4 — Chapter-opener variety

Classify the first sentence of each chapter into one of:
- Q (question): "Why…", "What if…", "How…"
- N (number/stat): "In 2008…", "Forty-three percent…"
- SV (subject-verb): "Honeyfund built…", "Banks make money…"
- IM (imperative): "Watch what happens…", "Look at this number…"
- AN (anecdotal): "When Sarah opened…", "On a Tuesday in…"

If any classification appears more than 2× in a single video → binary fail.

### Criterion 5 — Voice fingerprint match

Heuristic checks against [04_voice_canon.md](04_voice_canon.md):

- Contractions used? (≥ 3 instances) — +2 to score
- Active voice dominant? (≥ 80% of sentences) — +2 to score
- KateAsta signature phrases used? ("Here's what's actually happening",
  "Most people miss this", etc.) — +2 to score
- Sentence length cap respected? (no sentence > 28 words) — +2 to score
- Tone matches "explanatory investigation" not "salesy" or "academic" —
  +2 to score (subjective; producer scores honestly)

## Failure handling

Same as other gates:
- Critique loop revises targeting failed criterion.
- Max 3 cycles.
- After cap, soft-fail: emit best, log in critique_history, continue.

## Active rules (apply at stage start, populated from learnings logs)

(Empty initially. As pattern reviews promote learnings to Active Rules,
they get listed here per-stage. See learning logs 30–39.)
