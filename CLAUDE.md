# Skills Repository

A collection of reusable agent skills. Pure Markdown — no build tooling, no dependencies.

## Repo Structure

Each skill is a directory under `skills/` containing:

- `SKILL.md` — Full instructions, loaded on-demand when the agent invokes the skill.
- `INJECT.md` — Short always-on summary, injected into instruction files (`CLAUDE.md`, `AGENTS.md`) via `skills-inject`.

## SKILL.md Conventions

### Frontmatter

```yaml
---
name: skill-name
description: One or two sentences. Start with a verb. Explain what the skill does and when to use it.
argument-hint: "[path] [--flag]"   # Optional, only for command skills. Shows usage hint to the user.
allowed-tools: Bash(some-command)  # Optional, only if the skill needs specific tool permissions.
---
```

### Structure

Every SKILL.md follows this structure:

1. **`# Action-Based Title`** — Imperative, describes what the skill does (e.g. "Ship Code Using Git", "Add Missing Docblocks"). Not a noun or label.
2. **One-sentence intro paragraph** — A single sentence summarizing the skill. Keep it to one sentence.
3. **`## Key Rules`** — Hard constraints and safety guardrails as a flat bullet list. This section mirrors the INJECT.md content. Put the most important rules here — not buried in Guidelines or Command Process.
4. **`## Guidelines`** — Detailed guidance organized with `###` sub-sections. Structure varies per skill but should use a single `## Guidelines` heading rather than multiple top-level `##` sections.
5. **`## Command Process`** (optional) — For task-oriented skills that can be invoked as a command. Numbered steps prefixed with: "When invoked as a command, follow these steps:". Always-on skills (like the shipping skills) do not need this section. Command skills should include a `### Arguments` sub-section listing accepted arguments, followed by a `### Steps` sub-section with the numbered process.

## INJECT.md Conventions

### Frontmatter

```yaml
---
heading: Display Heading         # Optional, auto-derived from directory name if omitted.
priority: high                   # Optional: "high" | "normal" | "low", default "normal".
---
```

### Content

- Flat bullet list only — no sub-lists, no nested formatting.
- Content should be a subset of (or identical to) the `## Key Rules` section in SKILL.md.
- Avoid Markdown bold formatting (`**...**`). Use CAPS keywords for emphasis instead.

## Emphasis Conventions

Use CAPS keywords to emphasize hard constraints where violation causes real problems:

- `ALWAYS` — For mandatory actions (e.g. "ALWAYS use `npx changeset add --empty`").
- `NEVER` — For prohibited actions (e.g. "NEVER create changeset files manually").
- `MUST` — For requirements (e.g. "All exported functions MUST have JSDoc docblocks").
- `Do NOT` — For safety guardrails (e.g. "Do NOT modify real code outside of docblocks").

Do NOT use these on style guidance, soft recommendations, or general best practices. Reserve them for rules where breaking them causes broken builds, data loss, or incorrect behavior.

## Naming Conventions

- Lowercase, hyphen-separated: `shipping-git`, `review-gate`.
- Language-prefixed for technology-specific skills: `ts-docblocks`, `ts-readme`.

## Variants

`shipping-graphite` and `shipping-git` are mutually exclusive — they cover the same workflow with different tools. When updating one, check whether the same change applies to the other.
