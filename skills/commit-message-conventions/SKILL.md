---
name: commit-message-conventions
description: "Commit message conventions: the type(scope): subject format, standard commit types including revert, breaking-change markers, and how a structured history drives changelog generation and semantic versioning."
tags: [git, conventions, ci, changelog]
---

# Commit Message Conventions

A convention for writing commit messages that are both human-readable and
machine-parseable, so release tooling can generate changelogs and infer the next
semantic version automatically. (This is the Conventional Commits style.)

## Structure

```
<type>(<optional scope>): <subject>

<optional body>

<optional footer(s)>
```

- **type** — the category of change (required).
- **scope** — optional area affected, in parentheses, e.g. `fix(parser):`.
- **subject** — short imperative summary; no trailing period.

## Types

| Type | Meaning | Version bump |
| --- | --- | --- |
| `feat` | a new feature | MINOR |
| `fix` | a bug fix | PATCH |
| `docs` | documentation only | none |
| `style` | formatting, no code-meaning change | none |
| `refactor` | neither a fix nor a feature | none |
| `perf` | a performance improvement | PATCH |
| `test` | tests added or corrected | none |
| `build` | build system / dependencies | none |
| `ci` | CI configuration | none |
| `chore` | maintenance / tooling | none |
| `revert` | reverts a previous commit | none |

## Breaking changes

Mark a breaking change (MAJOR bump) either by appending `!` after the
type/scope (`feat(api)!: ...`) or with a `BREAKING CHANGE:` footer.

## Footers

Footers carry metadata: `BREAKING CHANGE: ...`, `Refs: #123`, `Reviewed-by: ...`,
`Co-authored-by: ...`. They follow a blank line after the body.

## Why it matters

A consistent, parseable history lets semantic-release / changesets compute the
next version and assemble a changelog with zero manual bookkeeping, and keeps
`git log` scannable by type and scope.

## Tooling note

Commitlint, Commitizen, and semantic-release all consume this format.
