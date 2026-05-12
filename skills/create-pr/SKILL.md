---
name: create-pr
description: Pull request workflow for coding agents—branch hygiene, atomic commits, conventional PR titles, reviewer-first descriptions, test plans, and risk notes. Use when opening a PR, drafting a GitHub/GitLab description, splitting work for review, or preparing a change for human reviewers.
---

# create-pr

Guidance for turning finished work into a **merge-ready pull request** that respects reviewers’ time and matches common engineering conventions.

## When to use this skill

- The user asks to **open a PR**, **draft a PR description**, or **prepare for review**
- A feature or fix is **done locally** and needs to be **packaged** for others
- Work should be **split** into smaller PRs for safer review

## Before you open the PR

1. **Branch** — Use a descriptive branch (examples: `feat/auth-magic-link`, `fix/checkout-total`, `issue-1234-session-timeout`).
2. **Scope** — Prefer **one logical change** per PR. If the diff is large or mixes concerns, split into follow-up PRs with a short note in each description linking the series.
3. **History** — Prefer **atomic commits** with **conventional** messages (`feat`, `fix`, `refactor`, `test`, `docs`, `style`, `chore`). Squash only when the project already does that by convention.
4. **Quality bar** — Run the project’s **format/lint/test** commands when they exist; fix failures before requesting review.
5. **Noise** — Do not commit secrets, large generated artifacts, or unrelated formatting churn.

## PR title

Use a single line, imperative mood, matching conventional style:

```text
type(scope): short description
```

Examples: `feat(auth): add magic link callback`, `fix(api): handle empty pagination cursor`.

If the repo does not use scopes, `type: description` is acceptable when that matches existing PRs.

## PR description (reviewer-first)

Write in **complete sentences**. Order sections roughly like this (omit empty sections):

1. **Summary** — What changed and **why** (problem or goal), in plain language.
2. **Implementation notes** — Non-obvious decisions, tradeoffs, or alternatives considered.
3. **How to test** — Exact commands or **numbered steps** a reviewer can follow.
4. **Risk / rollout** — Breaking changes, migrations, feature flags, or anything that could fail in production.
5. **Links** — Issue tracker IDs, design docs, or related PRs.

### What to avoid in commits and PRs

- Do **not** mention AI tools, assistants, or automated agents in commit messages, PR titles, or PR bodies.
- Do **not** use vague titles like “updates” or “fixes” without saying **what** and **where**.

## Optional extras

- **UI changes** — Describe what to look at; attach screenshots or short screen recordings when helpful.
- **API / schema changes** — Call out versioning, backwards compatibility, and example payloads.
- **Config / env** — List new variables with safe example values (never real secrets).

## After opening

- If CI fails, **fix or revert** before re-requesting review.
- Keep the PR description **updated** if the approach changes during review.
- Respond to feedback with **focused follow-up commits** (or a single amend/squash if that is the team norm).

## Checklist

- [ ] Title matches repo conventions and describes the change clearly
- [ ] Description explains motivation, approach, and how to verify
- [ ] Diff is scoped and easy to review
- [ ] Tests or manual test plan included where appropriate
- [ ] No sensitive data or unrelated files in the branch
