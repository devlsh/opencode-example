---
name: git
description: Use Git safely for common repository workflows including status inspection, staging, committing, branching, merging, rebasing, stashing, remotes, conflict resolution, undo and recovery. Trigger when asked to fix or inspect git state, prepare commits, sync branches, recover lost work, resolve merge or rebase issues, or choose the right git command sequence.
---

# Git Essentials

Use this skill to choose safe Git actions, not just to dump commands.

## Contract

This skill guarantees:

- Git advice starts from current repository state, usually `git status`.
- The least destructive workable command is preferred.
- Undo guidance distinguishes clearly between `restore`, `reset`, and `revert`.
- Shared-history risks are called out before rebase or force-push advice.

## Phases

1. Classify the task as inspection, normal workflow, sync, recovery, or history rewrite.
2. Check current state before suggesting a mutating action.
3. Pick the safest command family: `restore`, `reset`, `revert`, merge, rebase, stash, or branch.
4. Give the exact command sequence.
5. End with a verification step such as `git status`, `git diff`, or `git log --oneline --graph -n 10`.

## Output Format

Good output for this skill is:

- a brief statement of the safest approach
- the exact Git command sequence
- an explicit warning before destructive steps
- a quick verification command

Reference routing:

- everyday branch / commit / remote / sync flows → `references/basic-workflows.md`
- undo / reflog / recovery / conflicts / rebase trouble → `references/recovery.md`
- tags / cherry-pick / submodules / clean → `references/reference-commands.md`

## Anti-Patterns

- Jumping straight to `git reset --hard` without checking whether recovery is possible.
- Using `git push --force` when `--force-with-lease` would do.
- Recommending rebase on shared history without warning.
- Dumping commands without saying which option is safer.
- Treating Git as a cheat sheet when the user needs decision support.
