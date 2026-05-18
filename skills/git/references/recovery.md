# Git Recovery and Troubleshooting

## Inspecting history

```bash
# Show commit history
git log

# One line per commit
git log --oneline

# With graph
git log --graph --oneline --all

# Last N commits
git log -5

# Commits by author
git log --author="Name"

# Commits in date range
git log --since="2 weeks ago"
git log --until="2024-01-01"

# File history
git log -- file.txt
```

## Searching history

```bash
# Search commit messages
git log --grep="bug fix"

# Search code changes
git log -S "function_name"

# Show who changed each line
git blame file.txt

# Find commit that introduced bug
git bisect start
git bisect bad
git bisect good commit-hash
```

## Undoing working tree changes

```bash
# Discard changes in file
git restore file.txt
git checkout -- file.txt  # Old way

# Discard all changes
git restore .
```

## Undoing staged changes

```bash
# Unstage file
git restore --staged file.txt
git reset HEAD file.txt  # Old way

# Unstage all
git reset
```

## Undoing commits

```bash
# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Revert commit (create new commit)
git revert commit-hash

# Reset to specific commit
git reset --hard commit-hash
```

## Stashing

```bash
# Stash changes
git stash

# Stash with message
git stash save "Work in progress"

# List stashes
git stash list

# Apply latest stash
git stash apply

# Apply and remove stash
git stash pop

# Apply specific stash
git stash apply stash@{2}

# Delete stash
git stash drop stash@{0}

# Clear all stashes
git stash clear
```

## Rebasing

```bash
# Rebase current branch
git rebase main

# Interactive rebase (last 3 commits)
git rebase -i HEAD~3

# Continue after resolving conflicts
git rebase --continue

# Skip current commit
git rebase --skip

# Abort rebase
git rebase --abort
```

## Common issues

### Undo accidental commit

```bash
git reset --soft HEAD~1
```

### Recover deleted branch

```bash
git reflog
git checkout -b branch-name <commit-hash>
```

### Fix wrong commit message

```bash
git commit --amend -m "Correct message"
```

### Resolve merge conflicts

```bash
# Edit files to resolve conflicts
git add resolved-files
git commit  # Or git merge --continue
```

## Safety reminders

- Prefer `git revert` when undoing history already shared with others.
- Use `git reset --hard` only when you are certain local changes can be discarded.
- Use `git push --force-with-lease` instead of `--force`.
- Check `git status` before and after recovery operations.
