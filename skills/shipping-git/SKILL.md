---
name: shipping-git
description: Shipping workflow using standard Git and GitHub CLI. Provides always-on guidance for committing, branching, and creating PRs.
---

# Shipping Workflow (Git)

Always-on guidance for shipping code using standard Git and the GitHub CLI (`gh`). This skill teaches the agent how to create commits, branches, and pull requests following conventional workflows.

## Key Rules

- **Never commit, push, create branches, or create PRs without explicit user approval.**
- Before any git operation that creates or modifies a commit, present a review block containing: changeset content (if applicable), commit title, and commit/PR description. Wait for approval.
- Use standard `git add` and `git commit` workflows. Concise title on the first line, blank line, then description body.
- Use `gh pr create` for pull requests. Start PR descriptions with "This PR...".

## Git Workflow Details

### Creating Commits

Follow conventional commit message format:

```sh
git add -A
git commit -m "Commit title" -m "Description body explaining what changed and why."
```

- The first `-m` sets the commit title (first line). Keep it concise and descriptive.
- The second `-m` sets the commit body. Explain what changed and why.
- Use present tense, imperative mood (e.g. "Add feature" not "Added feature").

### Creating Branches

Create a descriptive branch name before committing:

```sh
git checkout -b feature/short-description
```

Common prefixes: `feature/`, `fix/`, `refactor/`, `docs/`, `chore/`.

### Creating Pull Requests

Use the GitHub CLI to create PRs:

```sh
gh pr create --title "PR title" --body "$(cat <<'EOF'
## Summary

This PR adds/fixes/updates...

- Bullet point describing a change.
- Another change.
EOF
)"
```

- Start PR descriptions with "This PR...".
- Use a `## Summary` section with concise bullet points.

### Pushing Changes

Push the branch and set the upstream:

```sh
git push -u origin HEAD
```

### Review Block Format

Before any git operation, present this review block and wait for approval:

1. **Changeset content** (if applicable) — the full changeset file contents.
2. **Commit title** — a concise title for the commit.
3. **Commit/PR description** — a short description that explains what changed and why.
