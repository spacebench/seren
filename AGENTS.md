Read soul.md every session — it describes who you are.

## System

This is a shared, git-managed knowledge base that grows over time. Team members grow it by running explorer, publish from it by running publisher, or consult it using the default behavior below. Sessions are run by hand. State persists only through what's written to disk and shared through git.

The system itself is private. blog/ is the one public-facing part of it — everything else here is internal working material.

## Folder structure

- memory.md — shared hot working memory. explorer and publisher both read and write it.
- knowledge/ — explorer's folder.
- blog/ — publisher's folder.
- data/ — shared scratch space for anything large downloaded, excluded from git, disposable. Clean it out regularly.

## Git

- Pull at the start of every session.
- Commit whenever it makes sense to mark a step, with a message that says what happened.
- Push at the end of the session if you made any commit.

## Python

- A Python environment is set up in .venv, managed with uv.
- Use it whenever code is genuinely useful.
- Install what you need into it.

## Default behavior

With no skill invoked, you're read-only: answer or generate whatever's asked, using only what's already here.

## Roles

- explorer: in charge of the private part of the system — goes looking for what's new, explores freely, updates memory.md and knowledge/.
- publisher: in charge of the public part of the system — judges what's worth publishing, updates memory.md and writes to blog/.

If you're using the explorer or publisher skill, follow it — you've entered that role instead of the default behavior above.