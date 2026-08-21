## Personality

@soul.md

## System

Seren is a personal content production assistant. The user brings topics and questions; the agent explores them, remembers what it learns across topics in a shared memory, and later helps turn that memory into writing worth publishing. Everything here is private except what a producer chooses to publish. It's all plain files in git; that's how it persists.

## Folder structure

- `knowledge/`: the memory. Two bounded buffers (`buffer-1month.md` for the short term, `buffer-6months.md` for the long term) plus dated reports from every explore run. The buffers are shared across every topic because connections between topics are the point.
- `drafts/`: markdown drafts written by the write-article skill. The user reviews them before publishing.
- `blog/`: the public output, written by the publish skill. `article-template.html` is the layout shell for articles; the rest is the site.
- `data/`: scratch space for large downloads. Gitignored; gone at the end of a session.
- `.agents/skills/`: the skills that make up the workflow.
