# Extended Git Command Reference

## Tags

```bash
# List tags
git tag

# Create lightweight tag
git tag v1.0.0

# Create annotated tag
git tag -a v1.0.0 -m "Version 1.0.0"

# Tag specific commit
git tag v1.0.0 commit-hash

# Push tag
git push origin v1.0.0

# Push all tags
git push --tags

# Delete tag
git tag -d v1.0.0
git push origin --delete v1.0.0
```

## Cherry-pick

```bash
# Apply specific commit
git cherry-pick commit-hash

# Cherry-pick without committing
git cherry-pick -n commit-hash
```

## Submodules

```bash
# Add submodule
git submodule add https://github.com/user/repo.git path/

# Initialize submodules
git submodule init

# Update submodules
git submodule update

# Clone with submodules
git clone --recursive https://github.com/user/repo.git
```

## Clean

```bash
# Preview files to be deleted
git clean -n

# Delete untracked files
git clean -f

# Delete untracked files and directories
git clean -fd

# Include ignored files
git clean -fdx
```

## Documentation

- Official docs: https://git-scm.com/doc
- Pro Git book: https://git-scm.com/book
- Visual Git guide: https://marklodato.github.io/visual-git-guide/
