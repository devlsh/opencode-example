# opencode

Shared `opencode` config repo for local skills, slash commands, MCP wiring, and operating conventions.

This repo is designed to live at `~/.config/opencode` and act as the source of truth for how `opencode` behaves on this machine.

## Overview

Current highlights:

- Plugin: `context-mode`
- Enabled MCP servers: `context7`, `github-grep`, `websearch`, `opensrc`, `context-mode`
- TUI theme: `system`

Core files:

| Path | Purpose |
| --- | --- |
| `opencode.json` | Main config for models, MCP servers, permissions, plugins, and commands. |
| `tui.json` | TUI theme configuration. |
| `AGENTS.md` | Repo-specific working rules for tool routing, context handling, and execution style. |
| `skills/` | Local skills available to `opencode`. |
| `commands/` | Local slash-command prompts available to `opencode`. |
| `me.json` | Local identity metadata used by this setup. |

## Quick Start

1. Clone this repo to `~/.config/opencode`.
2. Install `opencode`.
3. Copy `me.json.example` to `me.json` and set your name.
4. Fill in the required API keys in `opencode.json`.
5. Install any optional CLIs you want the skills to use.
6. Start or restart `opencode`.

```bash
mkdir -p ~/.config
git clone <your-repo-url> ~/.config/opencode
cp ~/.config/opencode/me.json.example ~/.config/opencode/me.json
```

If `opencode` is already running, restart it after changing config, skills, plugins, commands, or agents.

## Required Setup

This repo keeps placeholder `TODO:` values in `opencode.json` for MCP auth-related fields.

At minimum, set:

- `mcp.context7.headers.CONTEXT7_API_KEY`
- `mcp.websearch.headers.x-api-key`

Useful companion CLIs:

- [`gh`](https://cli.github.com/) for GitHub workflows
- [`jira`](https://github.com/ankitpokhrel/jira-cli) for Jira inspection
- [`jq`](https://jqlang.org/) for JSON parsing used by some skills
- [`context-mode`](https://www.npmjs.com/package/context-mode) for the local `context-mode` MCP server

## Repo Layout

```text
.
├── AGENTS.md
├── commands/
├── me.json
├── me.json.example
├── opencode.json
├── README.md
├── skills/
└── tui.json
```

## Installed Skills

Local skills currently available under `skills/`:

| Skill | Use case |
| --- | --- |
| `agent-browser` | Browser automation, scraping, screenshots, QA, and interactive app testing. |
| `conventional-commits` | Conventional emoji-prefixed commit messages from staged Git changes. |
| `copywriting` | Marketing copy for homepages, landing pages, pricing pages, and other conversion-oriented text. |
| `find-skills` | Discovery and installation help for additional skills. |
| `frontend-design` | High-quality frontend UI work for pages, components, dashboards, and other web surfaces. |
| `git` | Safe Git workflows for status, staging, commits, branches, merges, rebases, and recovery. |
| `github` | GitHub operations through `gh`, including PRs, issues, reviews, comments, releases, and CI inspection. |
| `jira` | Read-only Jira issue lookup and summarization through the local `jira` CLI. |
| `react-doctor` | React quality checks for lint, dead code, accessibility, bundle size, and architecture. |
| `seo-audit` | SEO diagnosis for ranking issues, indexing, metadata, Core Web Vitals, and crawl health. |
| `skill-creator` | Skill creation, editing, evaluation, and trigger tuning. |
| `vercel-composition-patterns` | React composition guidance for compound components, context providers, and avoiding boolean-prop sprawl. |
| `vercel-react-best-practices` | Vercel-oriented React and Next.js performance guidance for rendering, async work, bundle size, and data fetching. |
| `web-design-guidelines` | UI review against web interface and accessibility guidelines. |

To add a new local skill, create `skills/<skill-name>/SKILL.md` and document the trigger language clearly.

## Local Commands

Local slash commands currently installed under `commands/`:

| Command | What it does |
| --- | --- |
| `commit` | Stages intended Git changes, derives a commit message from the staged diff, and creates a commit without pushing. |
| `learn` | Extracts session learnings and writes them into the most relevant `AGENTS.md` files. |

Current command files:

- `commands/commit.md`
- `commands/learn.md`

To add another local slash command, create a markdown file under `commands/`.

You can also define config-level custom commands in `opencode.json`:

```json
{
  "command": {
    "example": {
      "description": "Example custom command",
      "prompt": "Do the thing"
    }
  }
}
```

## MCP Servers

Configured MCP servers in this repo:

| Server | Type | Purpose |
| --- | --- | --- |
| `context7` | remote | Up-to-date library and framework documentation lookup. |
| `github-grep` | remote | GitHub code search for real-world examples and patterns. |
| `websearch` | remote | Exa-backed web search. |
| `opensrc` | local | Fetches and inspects open-source package or repo source code. |
| `context-mode` | local | Sandbox execution, indexing, search, and context-preserving analysis. |

## Customization Notes

- Keep files in this repo under source control, then restart `opencode` to pick changes up.
- Use local skills for workflows you want available all the time.
- Keep skill descriptions explicit about both purpose and trigger phrases so routing stays reliable.
- Use `AGENTS.md` for repo-wide operating rules, especially tool-routing constraints.
- If you add commands or skills, update this README so the repo stays self-explanatory.

## Troubleshooting

- Treat `opencode.json` as sensitive local infrastructure. It may contain API-bearing config.
- If startup breaks after a config change, launch with `OPENCODE_DISABLE_PROJECT_CONFIG=1` and repair the repo config from a safe session.
