---
name: jira
version: 1.0.0
description: Inspect Jira issues safely through the local `jira` CLI. Use when asked to look up, summarize, filter, or inspect Jira tickets, status, assignees, backlog items, or JQL query results. In this workspace, this skill is read-only and should only use Jira listing or issue-view inspection paths.
triggers:
  - "look up this jira ticket"
  - "search jira issues"
  - "show my jira backlog"
  - "check jira status"
  - "run this jql"
tools:
  - exec
  - read
mutating: false
metadata:
  {
    "openclaw": {
      "emoji": "🧳",
      "requires": {
        "bins": ["jira"]
      }
    }
  }
---

# Jira

Use this skill to choose safe Jira inspection paths, not to dump CLI syntax. To determine the user's name, run: `jq -r '.name' ~/.config/opencode/me.json`. When requested to find things for them, use that name.

## Contract

This skill guarantees:
- Jira use in this workspace stays read-only.
- Commands are scoped as narrowly as possible by assignee, status, project, issue key, or JQL.
- Results are summarized instead of dumped raw.

## Phases

1. Classify the task as broad listing, filtered listing, or inspection of a specific issue.
2. Choose the narrowest read-only `jira issue` path that fits.
3. Add flags or JQL to scope the result.
4. Summarize the outcome clearly.

## Output Format

Good output for this skill is:
- the chosen read-only Jira command path
- the exact filter or issue scope
- the required token prefix reminder when relevant
- a short result summary rather than an unfiltered dump

References:
- everyday listing and issue-view patterns → `references/common-commands.md`
- read-only policy and output advice → `references/notes.md`

## Anti-Patterns

- Using create, edit, transition, comment, or other mutating Jira commands.
- Dumping a broad unfiltered issue list when the request is narrow.
- Treating Jira like a general project-management skill when this workspace only permits inspection.
