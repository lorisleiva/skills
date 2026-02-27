# Skills

A collection of reusable [Agent Skills](https://agentskills.io) for coding agents. Works with Claude Code, Cursor, Codex, and [40+ other agents](https://github.com/vercel-labs/skills#supported-agents).

## Install

```sh
npx skills add lorisleiva/skills
```

This copies SKILL.md files into your project's `.claude/skills/` (or equivalent agent directory). Commit them to git so your entire team gets the skills.

To install specific skills:

```sh
npx skills add lorisleiva/skills --skill shipping-graphite --skill changesets
```

## Available Skills

| Skill | Description |
|---|---|
| `shipping-graphite` | Graphite CLI workflow &mdash; `gt create`/`gt modify`, single commit per branch, stacked PRs. |
| `shipping-git` | Standard Git + GitHub CLI workflow &mdash; branches, commits, `gh pr create`. |
| `changesets` | Generate changeset files with changelog entries for package releases. |
| `ts-docblocks` | TypeScript JSDoc conventions and a scanner for missing docblocks. |
| `ts-readme` | Guidelines for writing developer-friendly TypeScript library READMEs. |
| `review-gate` | Human approval gate &mdash; requires review before any git operation. |

## INJECT.md

Each skill can include an optional `INJECT.md` file containing a short summary meant to be injected into your `CLAUDE.md` or `AGENTS.md` as always-on context. The agent doesn't need to load the full skill to follow these instructions.

Use [`skills-inject`](https://github.com/lorisleiva/skills-inject) to extract `INJECT.md` content and write it into your instruction files:

```sh
npx skills-inject
```

See the [`skills-inject` README](https://github.com/lorisleiva/skills-inject) for full usage.

### INJECT.md Format

```yaml
---
heading: Shipping (Graphite)   # Optional, auto-derived from directory name
priority: high                 # Optional: "high" | "normal" | "low", default "normal"
---

- Always-on instruction bullet one.
- Always-on instruction bullet two.
```

## Variants

Some skills are variants of the same concept:

- **`shipping-graphite`** and **`shipping-git`** are two approaches to shipping code. Install the one that matches your workflow.
- **`review-gate`** is complementary to either shipping skill. It adds an approval gate before any git operation.

## Contributing

Each skill is a directory under `skills/` containing:

- `SKILL.md` &mdash; Full skill instructions following the [Agent Skills spec](https://agentskills.io/specification).
- `INJECT.md` (optional) &mdash; Short summary for always-on injection into instruction files.

Skills should be self-contained and follow the naming conventions: lowercase, hyphen-separated, language-prefixed for technology-specific skills (e.g. `ts-docblocks`).
