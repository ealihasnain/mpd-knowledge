---
id: 09_gate_G12_slop
version: 1.0
updated: 2026-05-11
applies_to_stages: [3.1, 3.2, 3.6, 3.8, 3.9]
---

# Gate G12 — Anti-Slop Check

**Status:** v1.0 — threshold guidance refined. Soft-fail latitude on
subjective criteria (3 + 5) until D003 establishes baseline.

Runs after every text-generating stage (3.1, 3.2, 3.6, 3.8, 3.9).

## Criteria

| # | Criterion | Type | Threshold | Notes |
|---|---|---|---|---|
| 1 | Blocked-phrase count (Hard Ban list) | Binary | = 0 | Whitelist channel-specific allowlist from 05 |
| 2 | Concrete-fact density | Binary | ≥ 3 named entities or specific numbers per chapter | "Specific" excludes vague ("some", "many", "most"). Date counts. |
| 3 | Sentence-rhythm variety | Score 1–10 | ≥ 7 (soft-fail at < 5) | Sliding 4-sentence window word-count σ |
| 4 | Chapter-opener variety | Binary | No construction repeats >2× in a video | Per 05 classification: Q/N/SV/IM/AN |
| 5 | Voice fingerprint match | Score 1–10 | ≥ 7 (soft-fail at < 5) | KateAsta canon (04) heuristics |

## Implementation

### Criterion 1 — Blocked-phrase count

Fetch `05_voice_blocklist.md`. Run case-insensitive substring match against
the stage output for every entry in Category 1–4 (Hard Ban). Any hit = binary
fail unless the substring is part of a longer whitelisted phrase from the
channel-specific allowlist.

Worked example:
- Output: "Here's what's actually happening — they engineer the system…"
- Match check: "in essence" not present, "let me explain" not present, etc.
- Allowlist check: "Here's what's actually happening" IS whitelisted.
- Result: pass.

### Criterion 2 — Concrete-fact density

For each chapter:
- Count named entities: proper nouns (companies, persons, countries, places,
  branded products), but NOT pronouns and NOT category nouns
- Count specific numbers: dollar amounts, percentages, dates, named years,
  quantities with units (NOT "many", "most", "a lot")

Threshold: total ≥ 3 per chapter. Below 3 = binary fail with note: "Chapter
X has only N concrete anchors; needs ≥3."

### Criterion 3 — Sentence-rhythm variety

Sliding window of 4 consecutive sentences. Compute σ of word counts within
each window. Score:

| Std-dev σ | Window score |
|---|---|
| ≥ 8 | 10 |
| 6–8 | 8 |
| 4–6 | 6 |
| 2–4 | 4 |
| < 2 | 2 |

Stage criterion score = minimum window score across the output.

Soft-fail latitude: score 5–6 emits with warning in learning log Episode Log
(`FIX — rhythm flat at chapter X`). Score < 5 = binary fail, revision
required.

### Criterion 4 — Chapter-opener variety

Classify the first sentence of each chapter into Q / N / SV / IM / AN per
05's classification table. Count occurrences:

- ≤ 2 of any single code → pass
- 3+ of any single code → binary fail with note: "Chapters X, Y, Z all open
  with [code]; vary at least one."

### Criterion 5 — Voice fingerprint match

Heuristic scoring against `04_voice_canon.md`:

| Check | Points |
|---|---|
| Contractions used (≥3 instances) | +2 |
| Active voice dominant (≥80% of sentences) | +2 |
| KateAsta signature phrases used (any from allowlist in 05) | +2 |
| Sentence cap respected (no sentence >28 words) | +2 |
| Tone matches "investigative explainer" not "salesy" or "academic" | +2 |

10/10 = perfect canon match. 7/10 = pass. 5/10 = soft-fail with warning.
< 5 = binary fail.

## Failure handling

- Any binary fail → revise targeting failed criterion → re-evaluate.
- Score < 5 on Criterion 3 or 5 → revise.
- Score 5–6 on Criterion 3 or 5 → soft-fail latitude (emit with warning log).
- Cycle 3 reached with binary fail still active → soft-fail per global policy
  (`11_critique_checklist_global.md`).

## Active Rules (apply at stage start)

(Populated from learnings logs at runtime — see 30–39.)

## Calibration plan

After D003 (3 episodes shipped), measure G12 fire rate:

| Outcome | Action |
|---|---|
| G12 passes first try ≥ 70% of stages | Thresholds correct; lock |
| G12 fails first try > 50% of stages | Either prose actually is sloppy (good — fix prose) OR thresholds too strict (relax via mpd-patch) |
| Specific criterion fails > 80% consistently | Recalibrate that criterion specifically |

Pattern review reveals which.
