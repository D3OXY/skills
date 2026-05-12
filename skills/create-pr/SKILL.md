---
name: create-pr
description: Pull request workflow for coding agents—branch selection, GitHub CLI (gh pr create), tests before PR, confirmation flow, conventional titles, reviewer-first bodies. Use when opening a PR, drafting a GitHub description, or when the user asks in natural language what used to be the create-pr command (e.g. skip checks, yes without prompt, branch A to B).
---

# create-pr

This is an **agent skill** (discovered from `SKILL.md`). It is **not** a Cursor slash command. Apply it whenever the user wants a **real PR opened** or **PR copy drafted** with the workflows below.

Guidance for turning work into a **merge-ready pull request** and, when requested, executing **`gh pr create`** with the right branches and safeguards.

## When to use this skill

- The user asks to **open a PR**, **create a pull request**, **run create-pr**, or **draft a PR description**
- A feature or fix is **done locally** and needs to be **packaged** for review
- Work should be **split** into smaller PRs for safer review

## Mapping from legacy `/create-pr` behavior

If the user previously used a **`/create-pr`** command with arguments, interpret the same intent in **natural language**:

| User intent | Behavior |
| --- | --- |
| No branch named | PR from **current branch** → **default base** (infer `dev`, `main`, or repo default; ask if unclear) |
| One branch name | PR from **current branch** → that branch as **base** |
| Two branches, or `A -> B` / `A to B` | PR from **first** (head) → **second** (base) |
| Skip checks / `--skip-check` | Skip the **Run tests and checks** step |
| Yes / no prompts / `-y` / `--yes` | Skip the **confirmation** step before `gh pr create` |

Do **not** tell the user to type `/create-pr`; describe what you will do or ask for missing details in plain language.

---

## GitHub CLI workflow (when opening the PR)

Use this when the user wants an actual PR on GitHub (not only a description in chat).

### Step 1 — Determine branches

1. Current branch: `git branch --show-current`
2. From user text, resolve **source (head)** and **target (base)** per the table above
3. If the user is on the **base branch** with no explicit source/target, **stop** and say they should switch to a feature branch or name both branches

### Step 2 — Validate branch state

1. `git status --porcelain` — if dirty, **stop** and ask whether to commit, stash, or proceed
2. Confirm the **source** branch exists locally (or on remote if that is the workflow)

### Step 3 — Run tests and checks

**Skip this entire step** if the user asked to skip checks (`--skip-check`, “skip tests”, etc.).

1. Detect package manager (`pnpm-lock.yaml`, `yarn.lock`, `package-lock.json`, `bun.lockb`, etc.)
2. Prefer **scripts from `package.json`** (or `Makefile` / `pyproject.toml` / project docs) — do not invent tool invocations
3. Typical order when scripts exist: typecheck → lint/check → build → tests (and project-specific checks such as `knip` if present)
4. **Do not** start dev servers, watch mode, or long-running processes

### Step 4 — Push source branch

`git push -u origin <source-branch>` when commits are not yet on the remote.

### Step 5 — Gather PR context

1. `git fetch origin <target-branch>` (or full fetch if appropriate)
2. `git log origin/<target-branch>...<source-branch> --oneline`
3. `git diff origin/<target-branch>...<source-branch> --stat`

### Step 6 — Confirm (unless user waived)

Unless `-y` / `--yes` / explicit “go ahead without asking”:

Show **source → target**, commit count, and diff summary, then ask for confirmation before creating the PR.

### Step 7 — Create PR with GitHub CLI

After confirmation (or if user waived):

```bash
gh pr create --base <target-branch> --head <source-branch> --title "<title>" --body "$(cat <<'EOF'
## Summary
<concise bullets>

## Test plan
- [ ] …

EOF
)"
```

**Title:** conventional format `type(scope): description`; include issue `(#123)` when relevant.

### Step 8 — Finish

Return the PR URL, short summary, and suggested next steps (reviewers, CI). Open in browser when the environment allows (e.g. `open <url>` on macOS).

### Workflow discipline

- Prefer **only** the commands needed for this flow; do not run unrelated tooling
- No destructive git (e.g. force push) unless the user explicitly requests it and it is safe
- If a step fails, stop and report before continuing

---

## PR title and description (reviewer-first)

Use a single-line **title**, imperative mood:

```text
type(scope): short description
```

**Body** — complete sentences, optional sections:

1. **Summary** — what changed and why  
2. **Implementation notes** — tradeoffs, non-obvious choices  
3. **How to test** — commands or numbered steps  
4. **Risk / rollout** — migrations, flags, breaking changes  
5. **Links** — issues, designs, related PRs  

Do **not** mention AI tools in commits, titles, or PR bodies. Avoid vague titles (“fix stuff”, “updates”).

---

## Before you open the PR (general)

1. **Branch names** should be descriptive (`feat/…`, `fix/…`, `issue-1234-…`)
2. **Scope** — one logical change per PR when possible; link related PRs if split
3. **Commits** — conventional messages; follow repo squash/rebase norms
4. **Noise** — no secrets, no large unrelated churn

---

## Checklist

- [ ] Source and base branches are correct and confirmed with user when required  
- [ ] Checks run or intentionally skipped per user  
- [ ] Title and body match team conventions  
- [ ] PR URL returned after `gh pr create`  
