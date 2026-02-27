# Skills

A collection of reusable [Agent Skills](https://agentskills.io) for coding agents. Works with Claude Code, Cursor, Codex, and [40+ other agents](https://github.com/vercel-labs/skills#supported-agents).

## Install

> All examples use `pnpx`. You can also use `npx skills@latest`.

Browse the list below, then install:

```sh
pnpx skills add lorisleiva/skills
```

This copies SKILL.md files into your project's `.claude/skills/` (or equivalent agent directory). Commit them to git so your entire team gets the skills.

## Available Skills

| Skill | Description |
|---|---|
| `shipping-graphite` | Graphite CLI workflow &mdash; `gt create`/`gt modify`, single commit per branch, stacked PRs. |
| `shipping-git` | Standard Git + GitHub CLI workflow &mdash; branches, commits, `gh pr create`. |
| `changesets` | Generate changeset files with changelog entries for package releases. <br> _Command: `/changesets [patch\|minor\|major]`_ |
| `ts-docblocks` | TypeScript JSDoc conventions and a scanner for missing docblocks. <br> _Command: `/ts-docblocks [path] [--all]`_ |
| `ts-readme` | Guidelines for writing developer-friendly TypeScript library READMEs. <br> _Command: `/ts-readme [path]`_ |

## Always-on Context

Each skill includes a short summary (`INJECT.md`) of its most important rules. Use [`skills-inject`](https://github.com/lorisleiva/skills-inject) to write these summaries directly into your `CLAUDE.md` or `AGENTS.md`, so the agent follows them every turn without needing to load the full skill.

```sh
pnpx skills-inject
```

See the [`skills-inject` README](https://github.com/lorisleiva/skills-inject) for configuration and full usage.

## Variants

**`shipping-graphite`** and **`shipping-git`** are two approaches to shipping code. Install the one that matches your workflow.

## Contributing

Each skill is a directory under `skills/` containing:

- `SKILL.md` &mdash; Full skill instructions following the [Agent Skills spec](https://agentskills.io/specification).
- `INJECT.md` (optional) &mdash; Short summary for always-on injection into instruction files.

Skills should be self-contained and follow the naming conventions: lowercase, hyphen-separated, language-prefixed for technology-specific skills (e.g. `ts-docblocks`).
