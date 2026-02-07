---
name: conventional-commits
description: Draft and validate commit messages that comply with Conventional Commits 1.0.0. Use when writing git commit messages, enforcing commit format in reviews/CI, mapping commits to SemVer intent, or converting plain-language change notes into spec-compliant messages with optional scope, body, footers, and breaking-change markers.
---

# Conventional Commits

Use this skill to produce commit messages that follow the Conventional Commits 1.0.0 specification.
Use the official spec as the source of truth: https://www.conventionalcommits.org/en/v1.0.0/#specification

## Output Format

Write commit messages in this structure:

```text
<type>[optional scope][optional !]: <description>

[optional body]

[optional footer(s)]
```

Apply these REQUIRED rules:

1. Start with a type, then optional scope, optional `!`, then `: `.
2. Use `feat` for new features.
3. Use `fix` for bug fixes.
4. Put scope in parentheses when used, e.g. `fix(parser):`.
5. Place the description immediately after `: `.
6. Start body one blank line after the description.
7. Start footer block one blank line after body (or after description if no body).
8. Format each footer as `<token>: <value>` or `<token> #<value>`.
9. Use `-` in footer tokens instead of spaces, except `BREAKING CHANGE`.
10. Mark breaking changes with `!` before `:` and/or `BREAKING CHANGE: <description>` footer.
11. Keep `BREAKING CHANGE` uppercase when used.
12. Treat other structural units as case-insensitive when validating.

Apply these RECOMMENDED quality rules:

1. Write the description in imperative mood (for example `fix auth timeout`, not `fixed auth timeout`).
2. Keep the description concise so the header is easy to scan in `git log`.
3. Wrap body/footer lines at about 72 characters for terminal readability.
4. Use a body to explain why the change is needed when intent is not obvious from the diff.
5. Use explicit issue/action trailers when relevant (for example `Fixes: #123`, `Resolves: #77`, `Refs: #42`).

## Type Selection

Choose one primary type that best matches intent:

- `feat`: add behavior or capability
- `fix`: correct incorrect behavior
- `docs`: documentation-only change
- `style`: formatting-only change
- `refactor`: internal change without behavior fix/feature
- `perf`: performance improvement
- `test`: add or change tests
- `build`: build/dependency/tooling change
- `ci`: CI/CD pipeline change
- `chore`: maintenance that does not fit above
- `revert`: revert a previous change

Use types outside `feat` and `fix` when appropriate; only `feat`, `fix`, and breaking markers imply SemVer meaning by default.

## Drafting Workflow

1. Summarize what changed and why in one sentence.
2. Decide if the change is a feature, fix, or other type.
3. Choose a scope noun if it clarifies impact (`api`, `auth`, `parser`, `deps`).
4. Detect breaking behavior:
   - Add `!` before `:`, and/or
   - Add `BREAKING CHANGE: <description>` footer.
5. Write a concise description line.
6. Use imperative mood in the description and keep it standalone.
7. Add body paragraphs only when extra context is needed; wrap around 72 columns.
8. Add trailer footers for metadata (for example `Fixes: #123`, `Reviewed-by: Name`).
9. Re-check against the checklist below before finalizing.

## Validation Checklist

Confirm all items before returning a commit message:

1. Header matches `<type>[scope][!]: <description>`.
2. Description exists and is not empty.
3. Body and footer blocks are separated by exactly one blank line.
4. Footer tokens are valid trailers.
5. Breaking changes are explicitly marked (`!` or `BREAKING CHANGE:`).
6. `feat`/`fix` are used correctly when applicable.
7. Description uses imperative wording and is concise.
8. Body/footers are wrapped for readability when multi-line.

## SemVer Mapping

- `fix` -> PATCH
- `feat` -> MINOR
- Any commit with breaking change marker -> MAJOR

## Examples

```text
feat(auth): add device-bound refresh tokens
```

```text
fix(api): prevent duplicate invoice creation

Add idempotency key validation for create-invoice endpoint.

Refs: #482
```

```text
feat(storage)!: replace v1 blob schema

BREAKING CHANGE: remove support for legacy v1 blob readers.
```
