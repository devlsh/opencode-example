# GitHub Common Commands

## Pull requests and CI

```bash
# Check CI status on a PR
gh pr checks 55 --repo owner/repo

# List recent workflow runs
gh run list --repo owner/repo --limit 10

# View a run and see which steps failed
gh run view <run-id> --repo owner/repo

# View logs for failed steps only
gh run view <run-id> --repo owner/repo --log-failed
```

## JSON output

Most commands support `--json` and `--jq`:

```bash
gh issue list --repo owner/repo --json number,title --jq '.[] | "\(.number): \(.title)"'
```
