---
name: conventional-commits
description: "Write Conventional Commits — the type(scope): subject format, the common commit types, breaking-change notation, and how structured commit history enables automated changelogs and semantic-version inference."
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

- **type** — the kind of change (see below). Required.
- **scope** — an optional noun in parentheses naming the affected area, e.g. `feat(auth):`.
- **description** — a short, imperative summary ("add", not "added").

## Common types

| Type | Meaning | Version bump |
| --- | --- | --- |
| `feat` | a new feature | MINOR |
| `fix` | a bug fix | PATCH |
| `docs` | documentation only | none |
| `refactor` | neither fixes a bug nor adds a feature | none |
| `perf` | a performance improvement | PATCH |
| `test` | adding or correcting tests | none |
| `build` | build system or dependencies | none |
| `ci` | CI configuration | none |
| `chore` | tooling / maintenance | none |

## Breaking changes

Signal a breaking change in either of two ways — both trigger a MAJOR bump:

1. Append `!` after the type/scope: `feat(api)!: drop v1 endpoints`.
2. Add a footer: `BREAKING CHANGE: the v1 endpoints have been removed`.

## Examples

```
feat(parser): add array-literal support
fix(api): return 404 instead of 500 on missing skill
docs: clarify the breaking-change footer
refactor(auth)!: drop the legacy session cookie

BREAKING CHANGE: cookie-based sessions are removed; use bearer tokens.
```

## Why it matters

A structured history lets release tooling (semantic-release, changesets, etc.)
infer the next version and generate a changelog with no manual bookkeeping, and
makes `git log` scannable by type and scope.
