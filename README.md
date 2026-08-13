# Seren

A self-maintaining, git-based field monitor that follows a topic and writes what's worth knowing.

Seren is a coding-agent-driven field monitor. Point an agent at this repository and it can keep up with a field for you — reading what's new, remembering what it learns, and writing about what's actually worth your attention. Run it by hand whenever you want, or let the bundled GitHub Actions run it on a schedule. Everything lives in this repository as plain files you own.

## How it works

Everything here is plain files in a git repository: markdown notes, HTML and CSS for the blog. Nothing sits behind an API you don't control. Two skills define the whole workflow:

- **explore** — follows the field's actuality. Each run writes a dated report to `knowledge/` (the links it fetched and what it learned from them), then folds that report into two bounded buffers: `buffer-1month.md` for the live recent news and `buffer-6months.md` for the impactful events and long-term theses that set the editorial line. Reports older than six months are deleted; git keeps the archive.
- **publish** — reviews the two buffers (reaching into related reports when a story needs extra depth), decides what's worth sharing, and writes articles to `blog/` with each claim's source linked inline, the way a news article cites.

The skills are plain markdown in `.agents/skills/`, so they aren't tied to any one tool. Any coding agent that can read `AGENTS.md` and the skill files can run them — opencode, Claude Code (which picks the skills up from the `.claude/skills/` mirrors), or anything else. You invoke them however you like, and you commit whenever you want; git is how everything here persists.

If you'd rather the repository run itself, it ships with GitHub Actions ready to go: `explore` and `publish` run the same skills on a schedule (defaulting to opencode, committing and pushing for you), and `deploy` publishes `blog/` to GitHub Pages.

## Get started

1. **Create your repository.** Click "Use this template" above and pick a name.
2. **Clone it locally.**
3. **Tell Seren what you care about.** Replace the placeholder in `soul.md` with the field or topic you want it to follow. This one file makes the instance yours.
4. **Run it yourself.** Open the repository in your coding agent and ask it to explore — with opencode, that's `opencode run "/explore"`. The agent reads `soul.md`, follows the skill, and writes a dated report to `knowledge/`, folding what it learned into the two buffers. Try `/publish` too, to see what it turns into articles. Iterate on `soul.md` until the results match what you want, and commit and push whenever you're happy — you're in control.

Once it behaves the way you want, you can let it run on its own:

5. **Configure the workflows.** In your GitHub repository, go to Settings → Secrets and variables → Actions and add:

   | Type | Name | Value |
   |---|---|---|
   | Secret | `OPENCODE_API_KEY` | your API key |
   | Variable | `EXPLORE_MODEL` | model used by the explore workflow |
   | Variable | `PUBLISH_MODEL` | model used by the publish workflow |

6. **Enable GitHub Pages.** Settings → Pages → Source: **GitHub Actions** (not "Deploy from a branch"). This creates the `github-pages` environment the `deploy` workflow needs; without it, deployment fails.
7. **Test the workflows by hand.** From the Actions tab, run `explore` and `publish` manually a few times and check what lands in `knowledge/` and `blog/` before letting them run unattended.
8. **Turn on `deploy`.** Trigger it once you're happy with how the blog looks — it publishes `blog/` to GitHub Pages.
9. **Enable the schedule.** Each workflow file has a commented cron schedule (explore twice a day, publish once a day, deploy an hour after publish). Uncomment it once you trust the manual runs.

## Repository structure

- `AGENTS.md` — shared facts every skill relies on: folders, roles, how the repository is structured.
- `soul.md` — what this instance is passionate about. Edit this first.
- `knowledge/` — the memory: two bounded buffers (`buffer-1month.md`, `buffer-6months.md`) plus a dated report of every explore run. Reports older than six months are deleted; git is the permanent archive.
- `blog/` — the public output, written by the publish skill. Ships with a working default design; personalizing the colors, font, and page titles is the first thing the skill does.
- `data/` — scratch space for large downloads. Not tracked by git; disappears at the end of every session.
- `.agents/skills/` — the two skills, `explore` and `publish`, mirrored into `.claude/skills/` for agents that expect them there.
- `.github/workflows/` — the three GitHub Actions: `explore` and `publish` run the skills on a schedule, `deploy` publishes `blog/` to GitHub Pages.
