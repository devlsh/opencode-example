# Types and scope

## Table of contents

- Input requirements
- Commit types
- Scope guidance

## Input requirements

This skill expects the caller to provide staged diff context:

- `git diff --cached --stat`
- `git diff --cached --name-only`
- `git diff --cached`

## Commit types

Choose the dominant type:

- `✨ feat` for new features
- `🐛 fix` for bug fixes
- `🔨 refactor` for code restructuring without behavior change
- `📖 docs` for documentation-only changes
- `🚨 test` for adding or fixing tests
- `🧹 chore` for maintenance, dependencies, or config
- `🚀 perf` for performance improvements
- `🎨 style` for formatting or whitespace

## Scope guidance

Use a scope when one clear scope exists:

- single component or module, use that name
- multiple related files, use the parent directory or feature name
- broad mixed changes, omit scope

Pick one scope only. If scope is unclear or mixed, omit it.
