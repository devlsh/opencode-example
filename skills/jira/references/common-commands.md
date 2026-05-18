# Common commands

## Table of contents
- Required auth prefix
- List recent issues
- Filter by time, assignee, or status
- Use JQL
- View an issue
- Output modes

## List recent issues

```bash
jira issue list
```

## Filter by time, assignee, or status

Created in the last 7 days:

```bash
jira issue list --created -7d
```

Assigned to the current user (using the name from `~/.config/opencode/me.json`):

```bash
jira issue list -a "$(jq -r '.name' ~/.config/opencode/me.json)"
```

In backlog:

```bash
jira issue list -s "Backlog"
```

Rank order, matching UI more closely:

```bash
jira issue list --order-by rank --reverse
```

## Use JQL

Use JQL when simple flags are not enough.

```bash
jira issue list -q "summary ~ cli"
```

Prefer narrow JQL over very broad searches.

## View an issue

Basic issue view:

```bash
jira issue view LIV-1
```

Issue view with comments:

```bash
jira issue view LIV-1 --comments 5
```

## Output modes

Plain output:

```bash
jira issue list --plain
```

Raw output:

```bash
jira issue list --raw
```

CSV output:

```bash
jira issue list --csv
```
