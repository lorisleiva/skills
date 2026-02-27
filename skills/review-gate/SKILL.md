---
name: review-gate
description: Always-on instructions requiring human approval before any git operations. Ensures the agent never commits, pushes, or creates PRs without explicit permission.
---

# Review Gate

Always-on safety net that prevents the agent from performing any git operations without explicit human approval. This skill is complementary to shipping workflow skills but can be used standalone.

## Key Rules

- **Never** commit, push, create branches, or create PRs without explicit user approval.
- Before any git operation that creates or modifies a commit, present a **review block** containing:
    1. **Changeset content** (if applicable) — the full changeset file contents.
    2. **Commit title** — a concise title for the commit.
    3. **Commit/PR description** — a short description explaining what changed and why.
- Wait for the user to approve or request changes before proceeding.
- This applies to all of the following operations:
    - Creating commits or branches.
    - Running any commit command (`git commit`, `gt create`, `gt modify`, etc.).
    - Creating PRs via `gh pr create`, `gt submit`, or similar.
    - Creating or modifying changeset files (present the content for review before writing).

## When to Present a Review Block

Present a review block any time you are about to:

- **Create a commit** — whether via `git commit`, `gt create`, or any other tool.
- **Amend a commit** — e.g. `git commit --amend`, `gt modify`.
- **Create a branch** — when the branch creation is tied to a commit operation.
- **Push to a remote** — `git push`, `gt submit`, etc.
- **Create a pull request** — `gh pr create`, `gt submit`, or equivalent.
- **Write a changeset file** — present the proposed changeset content before writing it.

## Review Block Format

```
**Changeset** (if applicable):
---
'@scope/package-a': minor
---
Add support for custom themes.

**Commit title**: Add custom theme support

**Description**: This PR adds a theming API that allows users to customize
colors and typography. Includes default light and dark themes.
```

## What Does NOT Require a Review Block

- Reading files, searching code, running tests, or any read-only operation.
- Installing dependencies or running build commands.
- Making code changes in the working tree (these are reviewed at commit time).
- Git operations that don't create or modify commits (e.g. `git status`, `git log`, `git diff`).
