---
description: Smart commit with enforced conventional commit format
---

Stage the intended git changes, generate the commit message with the `conventional-commits` skill from the staged diff, and commit with that exact message. Do not push unless the user explicitly asks.

## Step 1: Stage intended changes

```bash
git add -A
```

## Step 2: Gather Context

```bash
# What's staged?
git diff --cached --stat
git diff --cached --name-only

# What branch are we on?
git branch --show-current
```

## Step 3: Analyze Changes

Read the staged diff to understand what changed:

```bash
git diff --cached
```

Then use the `conventional-commits` skill to generate the commit message from the staged diff.

Do not hand-write the commit subject.

## Step 4: Commit

Run the commit with the generated message.

```bash
git commit -m "<message>"
```

Only push when the user explicitly asks for it.
