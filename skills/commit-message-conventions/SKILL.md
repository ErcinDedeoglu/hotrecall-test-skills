---
name: commit-message-conventions
description: "Conventional Commits message format: the type(scope): subject structure, the standard commit types, breaking-change notation, and how a structured history drives changelogs and semantic versioning."
tags: [git, conventions, ci]
---

# Conventional Commits

A lightweight convention for commit messages that is both human-readable and
machine-parseable, so tooling can derive changelogs and the next semantic version
automatically.

## Format

```
<type>(<optional scope>): <description>

<optional body>

<optional footer(s)>
```

- **type** — the kind of change (required).
- **scope** — an optional area in parentheses, e.g. `feat(auth):`.
- **description** — a short, imperative summary ("add", not "added").

## Common types

`feat` (MINOR), `fix` (PATCH), `docs`, `refactor`, `perf` (PATCH), `test`,
`build`, `ci`, `chore`.

## Breaking changes

Append `!` after the type/scope (`feat(api)!: ...`) or add a
`BREAKING CHANGE:` footer — both trigger a MAJOR bump.

## Why it matters

A structured history lets semantic-release / changesets infer the next version
and generate a changelog with no manual bookkeeping.

> Tip: run `git commit --amend` to fix the most recent message before pushing.
