---
name: explore-topic
description: Explores a topic by spawning explorer subagents that write dated reports to knowledge/, then folds their findings into the shared memory.
---

## Subject

The subject comes from the chat, not a fixed field. Whatever the user is curious about, that's what you explore.

## Memory

Read both buffers before anything else. They are the memory so far: the one-month buffer holds what's happening now, the six-month buffer holds where things are heading. They shape how you frame the exploration and, later, how you fold it in.

## Explorers

The reading itself belongs to explorer subagents: they work in isolated contexts and write their reports themselves. Default to one explorer. Spawn several only when the subject has clearly distinct facets worth separate sweeps, one explorer per facet.

Each explorer task carries three things: the topic or facet, phrased so it stands alone; the path to write its report to, dated and slugged (like `knowledge/YYYY-MM-DD-<topic>.md`) and unique per explorer; and memory hints distilled from the buffers, the loose threads worth chasing and what's already known. Spawn the explorers in parallel and wait for all of them.

## Fold

When the explorers return, fold their notes into both buffers: integrate the new findings, prune what no longer matters, and keep the whole coherent across all topics. Forgetting is the job — memory that keeps everything remembers nothing. Keep each buffer's shape as written in its header.

When something suggests a connection or an open question — across topics or within one — write it into the six-month buffer as a thesis, noting the observation it grew out of. Every entry in either buffer carries the exact source URL it came from.

## Garbage collection

Reports are the trace of a moment, and a moment ages. Delete any report older than six months. The working tree stays a live memory; git keeps the archive.
