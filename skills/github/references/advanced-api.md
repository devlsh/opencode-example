# GitHub Advanced API Usage

Use `gh api` when higher-level subcommands do not expose what you need.

## Example

```bash
gh api repos/owner/repo/pulls/55 --jq '.title, .state, .user.login'
```

## Guidance

- Prefer `gh issue`, `gh pr`, and `gh run` first.
- Use `gh api` for uncommon fields, endpoints, or custom query shapes.
- Prefer filtering with `--jq` to keep outputs concise.
