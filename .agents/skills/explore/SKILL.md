---
name: explore
description: Explores a topic, reads widely, writes a dated report to knowledge/, and folds what it learned into the shared memory.
---

## Subject

The subject comes from the chat, not a fixed field. Whatever the user is curious about, that's what you explore.

## Files

`knowledge/` is yours. It holds two buffers and a row of dated reports. The buffers are the memory — shared across every topic. The reports are the trace of a single run.

## Knowledge cutoff

Your knowledge comes from training data with a cutoff date. There are two cases: things you don't know at all, and things you do know that may have moved on since the cutoff without you. Both are worth checking.

## Memory

The two buffers are the memory so far. The one-month buffer is what's happening now — build on it, chase its loose threads. The six-month buffer is where things are heading — let it shape what you pay attention to. Explore builds on what's already there: chase the connections between what's in memory and what the user is bringing now. That's the reason the memory is shared.

## Reading

Explore the way someone who actually follows this subject would — browsing what's recent and active (a listing, a feed, a known source's own output). What you care about is a scope, not a list of queries; a new name or method that matches none of your usual terms still belongs in it.

Read like someone doing a review, not an auditor — building a broad, working sense of what's happening and what it might mean. Take a finding as given and move to the next thing. If you catch yourself chasing one claim across source after source, that fixation is a poor trade against breadth — let the detail go and keep moving.

A source can be a PDF as well as a page — it downloads into `data/` and gets parsed for text (pdftotext or similar), so you read it like anything else.

## Sourcing

Every URL in a report is one you fetched during the run — the URL and what it says both come from the fetch. Training memory is the trap: a page you remember feels like knowledge, and a remembered URL paired with its remembered content produces a plausible finding you never actually saw. Memory can suggest where to look; only a fetch says what's there. If you know a source from before your cutoff, fetch it and confirm it still says what you think — content gets corrected, withdrawn, superseded. If a source resists access (paywall, rate limit, dead link), try the service's official API; if access still fails, say so and leave the gap. The absence of a source is information; an invented one is misinformation.

Be eager for the full range of sources — blogs, newsletters, forums, official outputs, specialist publications, alongside the obvious ones. A source you haven't read before is a find in its own right. A narrow range produces a narrow view — it's the mix that shows you the shape of a thing, not one outlet's version of it.

## Report

Each run ends in a report: a dated, uniquely-named file in `knowledge/`. It records the exact links you fetched — the URLs you actually visited, not homepages or search results — and what you learned from those documents, each finding carrying the URL it came from. The report is the raw material: it feeds the buffers, and it's what a later session turns to when a story needs extra depth.

## Ingestion

When the report is done, both buffers need to fold the new findings into what's already there, mixed across every topic and pruned of what no longer matters. Forgetting is the job — memory that keeps everything remembers nothing. Keep each buffer's shape as written in its header.

When something suggests a connection or an open question — across topics or within one — write it into the six-month buffer as a thesis, noting the observation it grew out of. Every entry in either buffer carries the exact source URL it came from.

## Garbage collection

Reports are the trace of a moment, and a moment ages. Delete any report older than six months. The working tree stays a live memory; git keeps the archive.
