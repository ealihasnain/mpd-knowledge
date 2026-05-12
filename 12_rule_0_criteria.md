---
id: 12_rule_0_criteria
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.1]
---

# Rule 0 — Topic Alignment Check (Stage 3.1 only)

Before producing the Strategy Brief, producer scores the requested topic
against the 4 channel criteria. Hard gate — failure here means the topic
gets reframed or rejected, not produced.

## The 4 criteria

### C1. Hidden pattern present?

Does this topic reveal an underlying mechanism, system, or psychological
pattern that most people miss? Not "a thing exists" but "this thing works
the way it does *because* of X."

**Pass example:** "Why 'Pay Yourself First' Doesn't Work for Most People"
— reveals that the advice misses the structural difficulty of expense
prediction in modern income volatility.

**Fail example:** "Top 10 Budget Apps for 2026" — list, no pattern.

### C2. Clear reframe moment available?

Can we identify a specific "You'd think X, but actually Y because Z" pivot
that the viewer can articulate after watching?

**Pass example:** You'd think "Pay Yourself First" works because it's
mathematically sound → actually it fails because it requires expense
predictability that most modern incomes lack → mechanism: variable income +
psychological accounting errors.

**Fail example:** "How to invest your first $1000" — instructional, no
reframe.

### C3. Sufficient depth without padding?

Can we produce 7–9 chapters of substantive content (≥3 named entities or
specific numbers per chapter, ≥80 datapoints total) without padding,
repetition, or filler?

**Pass example:** Pay Yourself First has documented research (1970s
behavioral economics), real cases (default contribution rates, 401k
participation studies), measurable failure rates, and modern adaptations
(round-up apps, automatic transfers).

**Fail example:** "Why Money is Important" — true but un-substantive; no
specific entities or numbers; chapters would be vague.

### C4. No advice / get-rich angle?

Is the framing investigation/explanation, NOT "do this to get rich" or
"buy this stock"?

**Pass:** "Here's why this widely-given advice often fails" — investigation.

**Fail:** "Do these 5 things to retire by 40" — advice.

## Scoring

Each criterion: pass (1) or fail (0). Sum = 0 to 4.

| Score | Producer behavior |
|---|---|
| **4/4** | Proceed silently to Strategy Brief generation. |
| **3/4** | Note which criterion borderline-failed in chat; proceed. |
| **2/4** | Propose stronger reframe before producing. Output: "TOPIC PARTIALLY ALIGNED — [criteria failed]. Suggested reframe: [reframe]. Proceed with reframe (yes/no)?" Wait for user. |
| **0–1/4** | STOP. Output: "TOPIC FLAGGED — [reasons]. This topic doesn't fit the channel without significant reframing. Suggested alternative angle: [reframe]. Or pick a different topic from queue.yml upcoming[]." |

## Worked example — D001 PayYourselfWrong

| Criterion | Score | Note |
|---|---|---|
| C1 Hidden pattern | 1 | Behavioral economics + income volatility = the pattern |
| C2 Reframe moment | 1 | Mathematically sound vs psychologically/structurally broken |
| C3 Depth | 1 | 1970s research + modern data + named cases (Vanguard 401k studies, etc.) |
| C4 No advice angle | 1 | Investigation, not prescription |

**4/4 → proceed silently.**

## Failure-mode examples

If a user triggers `Run stage 3.1 for D###` and that D### entry in queue.yml
is something like "Top 5 Crypto Picks for 2026":

- C1: fail (list, no pattern)
- C2: fail (no reframe)
- C3: depends (could have data but probably padding)
- C4: fail (advice/picks)

Score 1/4 → STOP. Output suggested reframe ("How Crypto Listing Mechanics
Actually Work" — investigation angle that meets C1, C2, C3, C4) and prompt
user.

## When this check runs

- **Always at start of stage 3.1** for any new D###.
- **Once per episode** — not on re-runs of 3.1 after mpd-patch edits.
- **Skipped on "resume flow"** if progress.md shows 3.1 already passed.
