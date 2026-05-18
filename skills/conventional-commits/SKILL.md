---
name: conventional-commits
description: Generate a conventional emoji-prefixed commit message from staged Git changes. Use when asked to write, suggest, or validate a commit message after reviewing staged Git changes.
---

# Conventional Commits

Use this skill to choose a coherent staged-change commit message, not to narrate every file.

## Contract

This skill guarantees:

- commit messages are based on staged changes only
- one dominant intent wins over exhaustive file-by-file narration
- scope is used only when it is genuinely clear
- the final subject is validated against the workspace format

## Phases

1. Review staged diff context.
2. Choose the dominant commit type.
3. Decide whether a clear scope exists.
4. Write a concise imperative subject.
5. Add a body only when it materially improves clarity.
6. Validate before returning the message.

## Output Format

Good output for this skill is:

- a single validated conventional-commit subject
- an optional body only when it helps explain why the change matters

References:

- type and scope selection → `references/types-and-scope.md`
- subject rules and examples → `references/format-and-validation.md`

## Anti-Patterns

- Basing the message on unstaged work.
- Overfitting the message to every changed file.
- Using an unclear scope just because one is available.
- Returning an unvalidated subject line.
