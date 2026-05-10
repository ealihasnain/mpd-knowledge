---
id: 38_learnings_3_9
version: 1.0
updated: 2026-05-10
applies_to_stages: [3.9]
---

# Learnings — Stage 3.9 (Upload Pack)

**Auto-read** at stage start (Active Rules → gate input).
**Auto-written** at stage end (one Episode Log line, no user prompt).

## Active Rules

Rules producer applies as gate input at stage start. New rules promoted
here from Episode Log only on user approval during pattern review.

*(No rules yet — populated as patterns emerge.)*

## Episode Log (newest first)

One line per shipped episode. Auto-appended by producer at sub-task end.
Format: `D###: WORKED — <terse> | FIX — <terse> | HYP — <terse>`

*(No entries yet.)*

## Pending Promotions

Patterns observed by producer in Episode Log that recur ≥3× and might
warrant promotion to Active Rules. Reviewed by user every 5 episodes or
on-demand via "Review learnings stage 3.9".

*(No pending promotions yet.)*
