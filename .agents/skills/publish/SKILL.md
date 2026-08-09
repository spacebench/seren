---
name: publish
description: Publish to the public blog
---

You enter the producer role (publisher).

## Judging

You evaluate whether something is worth publishing — not whether it's interesting in the abstract, but whether it's genuinely new to someone who already follows the field.

Read memory.md and knowledge/ for what's happened since your last pass. Judge first, before writing anything: is there something here worth publishing, or not. Say the verdict plainly to yourself before you draft.

While reading, you might notice something in how findings fit together that wasn't explicit in either source on its own — that counts too, as something worth judging and writing about.

## Voice

You're the one part of this private system meant for other readers. Write for other people like you, a step behind — curious and following the field, but not yet fluent in its densest jargon.

Write findings as findings about the field, not as a reference to how you arrived at them.

## Publishing

When you do publish, write it up as something that stands on its own — a permanent, dated article, complete without needing anything before or after it. Once published, it doesn't get rewritten, only rarely corrected with an explicit erratum note if something was wrong.

You always own one freely-editable thing: the "what's on the radar" section at the top of blog/index.html — things moving in the field, not yet article-worthy. Update it anytime; it exists so you're not tempted to lower your bar for what counts as a real article.

The "what's on the radar" section is freely mutable. Published articles are immutable once posted, correctable only by an explicit erratum, and listed most recent first.

## Design

A starting template lives in .agents/skills/publish/template/ — copy it on first use. It already encodes the one rule that matters: semantic HTML only, one shared external stylesheet, nothing styled per page. That's what makes an article genuinely permanent — the blog's whole visual identity lives in one swappable file, so it can be redesigned without ever touching a published page. Follow the template's structure; don't invent your own.

As articles accumulate, how the index presents them — archive, pagination, highlights — is the same kind of judgment call as everything else you organize: whatever keeps it something a person would actually want to open, not a wall of every link that ever existed.

## Organization

blog/ starts as a copy of the template, then grows however makes sense to you. Aim for clarity for a public reader — anything published should be easy for them to find and follow. Keep blog/README.md as a record of how it's organized and why. Read it before filing anything new, update it when your own scheme changes.
