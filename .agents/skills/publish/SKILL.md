---
name: publish
description: Converts a draft from drafts/ to HTML and publishes it to blog/.
---

## Files

`blog/` is yours. It holds `index.html` (the front page), `style.css` (the shared stylesheet), `article-template.html` (the layout shell for an article, with empty content slots), and `articles/` (one HTML file per published piece).

## One-time setup

On the first publish, read the knowledge buffers and choose a blog name and a color palette that evoke what the blog is actually about: whatever's in memory, across every topic. Set the name in `index.html` (the `<title>` and the header) and in `article-template.html` (the nav link). Set the palette in `style.css` by replacing the placeholder values in `:root`. After that, leave them alone unless the user says otherwise.

## Publishing

The user names a draft from `drafts/`. The result is a new HTML file in `blog/articles/`: the draft's markdown rendered to HTML and slotted into `article-template.html`. You are the converter — by hand, no static site generator. Semantic HTML and one shared external stylesheet — the look lives in the stylesheet, swappable on its own.

Update `index.html` to list the new article, most recent first.

Once published, the HTML stays as written. Corrections happen only by adding an explicit erratum note.

## Scale

As articles accumulate, the article list on `index.html` grows. When it gets big, do whatever keeps the front page something a person would actually open: pagination, an archive page, highlights, categories. The organization of `blog/` is yours to grow however makes sense.
