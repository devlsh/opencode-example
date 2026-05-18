# Format and validation

## Table of contents

- Commit shape
- Subject rules
- Validation regex
- Example

## Commit shape

With scope:

```text
<type>(<scope>): <short description>

<body - what and why, not how>
```

Without scope:

```text
<type>: <short description>

<body - what and why, not how>
```

## Subject rules

- keep the subject line at 72 characters or fewer
- use imperative mood
- do not end the subject with a period
- keep the message coherent and concise

## Validation regex

```text
^(✨ feat|🐛 fix|🔨 refactor|📖 docs|🚨 test|🧹 chore|🚀 perf|🎨 style)(\([^)]+\))?: .{1,72}$
```

If validation fails, regenerate or ask before proceeding.

## Example

```text
✨ feat(auth): implement proactive JWT token refresh mechanism

- Add refresh checks so expired sessions recover automatically
- Schedule refresh work before token expiry to reduce auth failures
- Handle refresh failure paths more cleanly for users
```
