# Basic Git Workflows

## Initial Setup

```bash
# Initialize repository
git init

# Clone repository
git clone https://github.com/user/repo.git
git clone https://github.com/user/repo.git custom-name
```

## Staging and committing

```bash
# Check status
git status

# Add files to staging
git add file.txt
git add .
git add -A  # All changes including deletions

# Commit changes
git commit -m "Commit message"

# Add and commit in one step
git commit -am "Message"

# Amend last commit
git commit --amend -m "New message"
git commit --amend --no-edit  # Keep message
```

## Viewing changes

```bash
# Show unstaged changes
git diff

# Show staged changes
git diff --staged

# Show changes in specific file
git diff file.txt

# Show changes between commits
git diff commit1 commit2
```

## Branch management

```bash
# List branches
git branch
git branch -a  # Include remote branches

# Create branch
git branch feature-name

# Switch branch
git checkout feature-name
git switch feature-name  # Modern alternative

# Create and switch
git checkout -b feature-name
git switch -c feature-name

# Delete branch
git branch -d branch-name
git branch -D branch-name  # Force delete

# Rename branch
git branch -m old-name new-name
```

## Merging

```bash
# Merge branch into current
git merge feature-name

# Merge with no fast-forward
git merge --no-ff feature-name

# Abort merge
git merge --abort

# Show merge conflicts
git diff --name-only --diff-filter=U
```

## Managing remotes

```bash
# List remotes
git remote -v

# Add remote
git remote add origin https://github.com/user/repo.git

# Change remote URL
git remote set-url origin https://github.com/user/new-repo.git

# Remove remote
git remote remove origin
```

## Syncing with remote

```bash
# Fetch from remote
git fetch origin

# Pull changes (fetch + merge)
git pull

# Pull with rebase
git pull --rebase

# Push changes
git push

# Push new branch
git push -u origin branch-name

# Force push (careful!)
git push --force-with-lease
```

## Common workflows

### Feature branch workflow

```bash
git checkout -b feature/new-feature
# Make changes
git add .
git commit -m "Add new feature"
git push -u origin feature/new-feature
# Create PR, then after merge:
git checkout main
git pull
git branch -d feature/new-feature
```

### Hotfix workflow

```bash
git checkout main
git pull
git checkout -b hotfix/critical-bug
# Fix bug
git commit -am "Fix critical bug"
git push -u origin hotfix/critical-bug
# After merge:
git checkout main && git pull
```

### Syncing fork

```bash
git remote add upstream https://github.com/original/repo.git
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

## Useful aliases

Add to `~/.gitconfig`:

```ini
[alias]
    st = status
    co = checkout
    br = branch
    ci = commit
    unstage = reset HEAD --
    last = log -1 HEAD
    visual = log --graph --oneline --all
    amend = commit --amend --no-edit
```
