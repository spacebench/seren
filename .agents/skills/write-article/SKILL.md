---
name: write-article
description: Spawns an article-writer subagent that drafts an article from memory into drafts/.
---

## Subject

If the user gave a theme, that's the subject. If not, read both buffers and pick the subject most worth writing about.

## Material

Material is file paths, never content. Always pass the two buffer paths; from under `knowledge/`, add the dated reports whose subjects relate to the article. The writer reads the files itself: summarizing or interpreting the material into the task would drag it back into your context, the thing this split exists to avoid.

## Draft

Spawn one article-writer subagent. Its task carries the subject, the path for the draft (dated and slugged, like `drafts/YYYY-MM-DD-<topic>.md`), and the material paths. Wait for it.

## Relay

Relay the writer's notes to the user with the draft's path. The draft waits for review; publishing is a separate step.
