# Notes

## Table of contents
- Workspace policy
- Statuses
- Query guidance
- Output guidance
- Anti-patterns

## Workspace policy

This workspace treats the Jira CLI as read-only.

Allowed paths:
- `jira issue list`
- `jira issue view`
- filtered variants of those commands
- JQL used through `jira issue list -q ...`

Do not use create, edit, transition, comment, or board-modifying flows here.

## Statuses

Known statuses include:
- `Open`
- `Blocked`
- `In Progress`
- `Code Review`
- `QA`
- `Ready`
- `Acceptance`
- `Done/Closed`

Treat these as useful filters, not rigid guarantees unless confirmed in current output.

## Query guidance

Prefer the narrowest useful query:
- assignee when asking about a person
- status when asking about workflow stage
- recent time filters when asking what changed
- JQL only when normal flags are not enough

## Output guidance

Prefer summarizing results over pasting raw issue lists.

Good summary shape:
- what was queried
- how many items matched
- the most relevant issues
- any obvious blockers, priorities, or patterns

## Anti-patterns

Avoid:
- broad unfiltered issue dumps
- mutating workflows
- assuming status semantics without checking actual issue output
- using JQL for everything when normal flags are clearer
