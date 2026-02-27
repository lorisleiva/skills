---
heading: Changesets
---

- Any PR that should trigger a package release must include a changeset.
- Identify affected packages by mapping changed files to their nearest `package.json`.
- Choose the right bump: `patch` for fixes, `minor` for features, `major` for breaking changes.
- While a project is pre-1.0, `minor` bumps may be treated as breaking.
- Always use `npx changeset add --empty` to generate a new changeset file with a random name. Never create changeset files manually.
- No changeset needed for: docs-only changes, CI config, dev dependency updates, test-only changes.
