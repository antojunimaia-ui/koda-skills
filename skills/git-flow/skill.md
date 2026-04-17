---
name: git-flow
version: 1.0.0
description: Conventional commits, branch naming, PR descriptions, and git workflow automation.
triggers: [commit, branch, pr, pull request, git]
---

You are operating in **Git Flow** mode. Apply these standards to all git operations in this session.

## Commit Messages (Conventional Commits)

Format: `<type>(<scope>): <description>`

Types:

- `feat` — new feature
- `fix` — bug fix
- `refactor` — code change that neither fixes a bug nor adds a feature
- `perf` — performance improvement
- `style` — formatting, missing semicolons, etc. (no logic change)
- `test` — adding or updating tests
- `docs` — documentation only
- `chore` — build process, dependency updates, tooling
- `ci` — CI/CD configuration

Rules:

- Description in lowercase, imperative mood ("add feature" not "added feature")
- Scope is optional but recommended for large projects
- Breaking changes: add `!` after type (`feat!:`) and explain in body
- Keep subject line under 72 characters

Examples:

```
feat(auth): add OAuth2 login with Google
fix(api): handle null response from payment gateway
refactor(components): extract Button into shared library
chore: update dependencies to latest patch versions
```

## Branch Naming

- `feat/short-description` — new features
- `fix/issue-description` — bug fixes
- `refactor/what-changed` — refactoring
- `chore/task-name` — maintenance tasks
- Use kebab-case, keep it short and descriptive

## PR Descriptions

Structure:

1. **What** — one sentence summary of the change
2. **Why** — the problem being solved or motivation
3. **How** — brief technical approach (optional for small PRs)
4. **Testing** — how it was tested

## Workflow

- Always work on a branch, never commit directly to `main`
- Squash commits before merging if the branch has noisy WIP commits
- Tag releases with semantic versioning: `v<major>.<minor>.<patch>`
