---
id: 29_stage_3_10_library
version: 1.0
updated: 2026-05-12
applies_to_stages: [3.10]
---

# Stage 3.10 — Library Update

## Producer's role

Final pipeline stage. Updates the corpus index with any new assets, bumps
version, then prompts "published?" to trigger the completion handshake.

No new artifact file — this stage UPDATES `06_corpus_index.md` in place.

## Inputs

- `06_VideoHTML_v#.html` from Stage 3.6 — the NEW ASSETS FOR LIBRARY
  manifest section
- `06_corpus_index.md` — current corpus state (will be modified)

## Update operations

### 1. Append new asset rows

For each new asset listed in 06_VideoHTML's manifest, add a row to the
corpus's "Asset Library" section:

```markdown
| Asset | Category | First Used | File |
|---|---|---|---|
| Warren Buffett portrait | portrait | D012 PayYourselfWrong | portrait_warrenBuffett_v1.svg |
```

### 2. Update episode entry status

In the 46-week table, find the row for D### and mark as shipped:

```markdown
| 03 | May 11 | Pay Yourself Wrong ([D001 — shipped 2026-05-11](#)) | P1 | EVERGREEN |
```

(The shipped marker can be a link to the video, added in step 4 if URL provided.)

### 3. Bump corpus version stamp

In the YAML frontmatter of 06_corpus_index.md:

```yaml
version: 1.0  →  version: 1.1
updated: 2026-04-30  →  updated: 2026-05-11
```

### 4. Zero-asset week note (if no new assets)

If the video reused all assets from the library, the corpus changelog gets
a note:

```markdown
## v1.X — D### shipped (no new assets)
Episode reused all visual assets from existing library. Library row count unchanged.
```

## G11 check

Pass condition:
- Either at least one new asset row added to corpus, OR
- Explicit "zero new assets" note in changelog

Silent skip (neither condition met) = G11 binary fail.

## After update emission

Producer:

1. Emits updated 06_corpus_index.md as download.
2. Updates progress.md → 3.10 status `passed`, Active Episode status →
   `awaiting_publish_confirmation`.
3. Auto-writes 39_learnings_3_10.md Episode Log line.
4. Emits the three downloads (corpus, progress, learning log).
5. Outputs the publish-prompt:

```
═══════════════════════════════════════════════════════
D### PIPELINE COMPLETE — All 10 stages passed.

Has the video been published to YouTube?

  Reply "yes published [URL]" → I'll dump D### to 99_changelog.md,
    reset progress.md, promote next episode from queue.yml.

  Reply "not yet" → progress.md preserved. Resume when ready by
    typing "resume flow" in any new chat.
═══════════════════════════════════════════════════════
```

## On "yes published"

(Detailed flow in SKILL.md §Pipeline completion. Summary: append D### record
to 99_changelog.md, reset progress.md to clean state, promote next episode
from queue.yml upcoming[] to active{}.)

## On "not yet"

Leave progress.md as-is. User can resume later or re-edit any stage.

## Failure modes

- **Manifest missing from VideoHTML:** G7a should have caught this at 3.6.
  If somehow it slipped through, prompt user to add the section to the
  VideoHTML or to confirm "zero new assets".
- **Asset naming convention violation:** flag and request rename before
  appending. (`fixturename` not allowed; should be `category_shortName_v1.svg`.)
- **Episode entry not found in corpus:** the topic was added to queue.yml
  but never to 06_corpus_index.md. Producer asks user whether to add it
  retroactively or leave the corpus as-is.
