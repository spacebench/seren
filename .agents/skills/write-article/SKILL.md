---
name: write-article
description: Spawns an article-writer subagent that drafts an article from memory into drafts/.
---

## Subject

If the user gave a theme, that's the subject. If not, read both buffers and pick the subject most worth writing about.

## Material

The writer draws only on what the task hands it. The two buffers are always material; from the `knowledge/` listing, add the dated reports whose subjects relate to the article.

## Draft

Spawn one article-writer subagent. Its task carries the subject, the path for the draft (dated and slugged, like `drafts/YYYY-MM-DD-<topic>.md`), and the material paths. Wait for it.

## Relay

Relay the writer's notes to the user with the draft's path. The draft waits for review; publishing is a separate step.
