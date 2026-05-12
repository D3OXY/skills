# skills

A **multi-skill** [agent skills](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/overview) repository: each folder under `skills/` is one installable capability for coding agents (Claude Code, Cursor, Copilot, and others via the [Skills CLI](https://github.com/vercel-labs/skills)).

## Skills in this repo

| Skill | Summary |
| --- | --- |
| [`d3-design`](skills/d3-design/) | UI / frontend design philosophy: universal principles plus an on-request cinematic floating-glass aesthetic (`SKILL.md`, `cinematic-aesthetic.md`, `blueprints.md`). |
| [`create-pr`](skills/create-pr/) | Pull request workflow: branch hygiene, conventional titles, reviewer-first descriptions, test plans, and review checklist. |

List what the CLI would install without downloading:

```sh
npx skills add YOUR_GITHUB_USER/skills --list
```

Install **one** skill by name (recommended for focused installs):

```sh
npx skills add YOUR_GITHUB_USER/skills --skill d3-design
npx skills add YOUR_GITHUB_USER/skills --skill create-pr
```

Install **several** skills in one command:

```sh
npx skills add YOUR_GITHUB_USER/skills --skill d3-design --skill create-pr
```

Install **all** skills from this repository (non-interactive):

```sh
npx skills add YOUR_GITHUB_USER/skills --all --yes
```

Replace `YOUR_GITHUB_USER` with your GitHub username or organization. If you install from a **renamed** GitHub repo named `skills`, the shorthand is `owner/skills`.

You can also install from a **subpath** when a host supports it, for example a single skill directory (see [Skills CLI](https://github.com/vercel-labs/skills) docs for URL formats).

### Verify

- **Claude Code:** `/skills` should list installed skills after add.
- **Cursor:** skills land per the CLI’s agent rules; confirm the skill appears in your skills or rules UI after installation.

## Repository layout

```text
skills/
  d3-design/
    SKILL.md
    cinematic-aesthetic.md
    blueprints.md
  create-pr/
    SKILL.md
LICENSE
README.md
```

Each skill’s **`SKILL.md`** includes YAML frontmatter (`name`, `description`) used for discovery and activation.

## Renaming this repo on GitHub

If you are migrating from a single-skill repo (for example `d3-design`) to this **`skills`** umbrella:

1. On GitHub: **Settings → General → Repository name** → rename to `skills` (or your chosen name).
2. Update **About** description, for example: *Agent skills pack: UI design philosophy (d3-design) and PR workflow (create-pr). Install with `npx skills add owner/skills`.*
3. Update any badges, links, or registry entries that still pointed at the old repo name.

Local clone:

```sh
git remote set-url origin https://github.com/YOUR_GITHUB_USER/skills.git
```

## Forking and customization

Skills are meant to be **forked**. Adjust copy, checklists, or tokens to match your team; keep `name` in frontmatter aligned with the folder name if you rely on `--skill` installs.

## License

MIT — see [LICENSE](LICENSE).

## Author

[D3OXY](https://github.com/D3OXY)
