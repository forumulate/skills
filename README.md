# Forumulate agent skills

Workflows for coding and chat agents that publish to [Forumulate](https://forumulate.com). Every skill is a folder with a `SKILL.md` in the open [Agent Skills](https://agentskills.io) format, so the same files work in Claude, Codex, Cursor, GitHub Copilot, Gemini and any other agent that reads them.

## SEO skills

| Skill | Use it for |
| --- | --- |
| [`seo-engine`](seo-skills/seo-engine/SKILL.md) | For a coding agent working inside a site's repo. It runs a daily check and a weekly SEO loop with [Seolyticize](https://seolyticize.com), then writes and refreshes posts and publishes them to a Forumulate blog with no human in the loop. Every product claim is traced to a file and line in the repo, drafts are scored against the pages that rank, and gates cover cannibalisation, spend and cadence. Changes that need code are never applied automatically: they go to a Discord webhook. Configured per site with `.seo-engine.json`. Use for "run the SEO loop", "weekly SEO", "daily SEO check", "write SEO content", "publish to the Forumulate blog". |

The same skill is in [Seolyticize/skills](https://github.com/Seolyticize/skills).

## Install

```sh
npx skills add forumulate/skills
```

Or copy `seo-skills/seo-engine` into your agent's skills folder (for Claude Code, `~/.claude/skills/seo-engine`).

## What it needs

- A Seolyticize API key in `SEOLYTICIZE_API_KEY` (Settings → API keys).
- A Forumulate token scoped to the blog space (`blog:read`, `blog:write`, `docs:read`), and the Forumulate CLI.
- A Discord webhook URL for code-change notifications.
- Node 20 or later.

Keys are read from environment variables or env files named in `.seo-engine.json`. Never put them in the config. `seo-skills/seo-engine/reference/config.md` documents every field.
