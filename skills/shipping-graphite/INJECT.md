---
heading: Shipping (Graphite)
---

- **Never commit, push, create branches, or create PRs without explicit user approval.**
- Before any git operation that creates or modifies a commit, present a review block containing: changeset content (if applicable), commit title, and commit/PR description. Wait for approval.
- Use `gt create -am "Title" -m "Description body"` for new PRs. The first `-m` sets the commit title; the second sets the PR description.
- Use `gt modify -a` to amend the current branch with follow-up changes (never create additional commits on the same branch).
- Escape backticks in commit messages with backslashes for shell compatibility (e.g. `"Update \`my-package\` config"`).
- Start PR descriptions with "This PR...".
