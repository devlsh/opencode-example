---
name: github
description: Work with GitHub repositories through the `gh` CLI for issues, pull requests, reviews, comments, workflow runs, releases, and repository inspection. Use when asked to look up, summarize, create, update, review, merge, label, triage, or investigate GitHub items, including CI failures and advanced API queries.
---

# GitHub Skill

Use this skill to choose the right GitHub CLI path, not to dump command syntax blindly.

## Contract

This skill guarantees:

- GitHub tasks prefer the highest-level `gh` command that fits.
- Structured output with `--json` and `--jq` is used when summarization or reasoning matters.
- Commands stay scoped to the relevant repository, PR, issue, workflow run, or release.
- `gh api` is reserved for cases where standard subcommands are insufficient.

## Phases

1. Classify the task as issues, pull requests, CI/workflows, repository inspection, or advanced API work.
2. Choose the narrowest `gh` subcommand that covers it.
3. Add `--repo owner/repo` when outside the target checkout.
4. Escalate to `gh api` or GraphQL only when needed.
5. Summarize the result in a filtered, readable way.

## Output Format

Good output for this skill is:

- the chosen `gh` path
- the exact scoped command
- filtered JSON fields when relevant
- a short note about any caveat or follow-up verification

Reference routing:

- common PR / issue / workflow patterns → `references/common-commands.md`
- uncommon endpoints and custom queries → `references/advanced-api.md`
- parent/sub-issue hierarchy → GraphQL with `GraphQL-Features: sub_issues`

## Anti-Patterns

- Using `gh api` for tasks already covered by `gh issue`, `gh pr`, or `gh run`.
- Omitting `--repo owner/repo` when context is ambiguous.
- Returning huge unfiltered blobs when `--json` and `--jq` would make the result readable.
- Jumping into raw logs or APIs before checking the higher-level GitHub object first.
