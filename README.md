# Seren

Seren is a git-based content production assistant: explore, remember, write. By hand or on a schedule.

You bring the topics and questions you're curious about, and the agent explores them, remembers what it learns across topics in a shared memory, and later helps turn that memory into writing worth publishing. It runs by hand, or unattended on a schedule when you want it to. Everything lives in this repository as plain files you own: markdown notes, markdown skills, HTML and CSS for the blog.

## How it works

Three skills make up the workflow:

- **explore** takes a topic and reads widely across whatever's recent and active: listings, feeds, known sources, blogs, newsletters, official outputs. It writes a dated report to `knowledge/` recording the exact links it fetched and what it learned from each, then folds that report into two bounded buffers: `buffer-1month.md` for the live recent news, and `buffer-6months.md` for the impactful events and longer theses that set the editorial line. Reports older than six months are deleted; git keeps the archive.
- **write-article** drafts an article from memory into `drafts/`. The two buffers are its material. It doesn't explore anew. The draft is a plain markdown file you read and revise before it goes anywhere.
- **publish** takes a named draft from `drafts/` and converts it to HTML in `blog/`, with each claim's source linked inline where it appears. The blog ships with a working default design. On the first publish, the agent reads the memory and sets a name and color palette that fit what the blog is actually about.

Seren keeps one growing memory across every topic, so a finding about one subject can connect to a finding about another. Those connections are the point.

The skills are plain markdown in `.agents/skills/`, and `AGENTS.md` holds the shared instructions. Any coding agent that reads `AGENTS.md` and the skill files can run them. `CLAUDE.md` and `.claude/skills/` mirror those for Claude Code. The bundled GitHub Actions use opencode. Bring whichever agent you like.

## Manual first, automatable on top

Seren is built to be run by hand. You bring whatever's on your mind, the assistant explores it, fetches sources, connects what it finds to what's already in memory, and helps turn it into writing. That core loop stands on its own.

If you want some or all of that to happen unattended, the repository ships with one ready setup: opencode driven by GitHub Actions, exploring a fixed topic on a schedule and turning what accumulates into articles. It's just a starting point. The skills are plain markdown and the memory is plain files, so you can drive them with any agent and any scheduler, or none at all.

And it isn't either/or. A natural way to use Seren is to keep exploring by hand day to day, chasing whatever you're curious about, while a schedule quietly monitors one steady topic in the background. Both write to the same `knowledge/` buffers, so each session picks up what the other gathered.

## Get started

1. **Create your repository.** Click "Use this template" above and pick a name.
2. **Clone it locally.**
3. **Set the persona.** Open `soul.md` and shape the agent's persona (the default is fine to start).
4. **Explore a topic.** With opencode: `opencode run "/explore <your topic>"`. The agent reads the skill, fetches sources, writes a dated report to `knowledge/`, and folds what it learned into the two buffers.
5. **Write an article.** A good manual flow: ask the agent what articles it could propose from memory, pick one, then `opencode run "/write-article <subject>"`. It drafts into `drafts/`. Open it and read it.
6. **Publish.** `opencode run "/publish <path-to-draft>"`. It renders the draft to `blog/` and lists it on the front page.
7. **Iterate.** Tweak `soul.md` and your prompts until the output matches what you want; commit and push when you're happy.

Once it behaves the way you want, you can let part of it run on its own:

8. **Configure the workflows.** In your GitHub repository, go to Settings → Secrets and variables → Actions and add:

   | Type | Name | Value |
   |---|---|---|
   | Secret | `OPENCODE_API_KEY` | your API key |
   | Variable | `EXPLORE_MODEL` | model used by the explore workflow |
   | Variable | `PUBLISH_MODEL` | model used by the publish workflow |

9. **Set the topic for scheduled runs.** Put the topic you want monitored on each run into `prompts/explore.txt`. The explore workflow reads this file; it fails early if you leave the `[topic to explore]` placeholder in place.
10. **Enable GitHub Pages.** Settings → Pages → Source: **GitHub Actions** (not "Deploy from a branch"). This creates the `github-pages` environment the deploy workflow needs.
11. **Test the workflows by hand.** From the Actions tab, run `explore`, `publish`, and `deploy` manually a few times and check what lands in `knowledge/`, `blog/`, and on Pages before letting them run unattended.
12. **Turn on the schedule.** Each workflow file has a commented cron schedule (defaults: explore twice a day, publish once a day, deploy an hour after publish). Uncomment it once you trust the manual runs, or throw the workflows out and wire up your own. The skills don't care.

## How the bundled automation works

The shipped workflows run the same skills you'd run by hand:

- **explore** reads the topic from `prompts/explore.txt`, runs `/explore`, and commits and pushes the result.
- **publish** runs `/write-article`, detects the new draft in `drafts/`, then runs `/publish <draft>` and commits everything.
- **deploy** publishes `blog/` to GitHub Pages.

## Repository structure

- `AGENTS.md`: the agent instructions (folders, roles, how the repository is structured).
- `soul.md`: the agent's persona.
- `prompts/explore.txt`: the topic for scheduled explore runs.
- `knowledge/`: the memory. Two bounded buffers (`buffer-1month.md`, `buffer-6months.md`) plus a dated report of every explore run.
- `drafts/`: markdown drafts written by write-article. You review them before publishing.
- `blog/`: the public output, written by publish. Ships with a working default design.
- `data/`: scratch space for large downloads, gitignored and gone at the end of a session.
- `.agents/skills/`: the three skills (`explore`, `write-article`, `publish`), mirrored into `.claude/skills/` for Claude Code.
- `.github/workflows/`: the bundled GitHub Actions (`explore`, `publish`, `deploy`), one predefined setup you can replace.
