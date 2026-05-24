# skills

A **multi-skill** [agent skills](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/overview) repository: each folder under `skills/` is one installable capability for coding agents (Claude Code, Cursor, Copilot, and others via the [Skills CLI](https://github.com/vercel-labs/skills)).

**Repository:** [github.com/D3OXY/skills](https://github.com/D3OXY/skills)

## Skills in this repo

| Skill | Summary |
| --- | --- |
| [`d3-design`](skills/d3-design/) | UI / frontend design philosophy: universal principles plus an on-request cinematic floating-glass aesthetic (`SKILL.md`, `cinematic-aesthetic.md`, `blueprints.md`). |
| [`create-pr`](skills/create-pr/) | **Agent skill** (not a slash command): PR workflow including optional `gh pr create`, branch resolution, checks, confirmation, titles, and bodies. |
| [`ubiquitous-language`](skills/ubiquitous-language/) | Extracts a DDD-style domain glossary from the current conversation, flags ambiguities, and writes `UBIQUITOUS_LANGUAGE.md`. |

List what the CLI would install without downloading:

```sh
npx skills add D3OXY/skills --list
```

Install **one** skill by name (recommended for focused installs):

```sh
npx skills add D3OXY/skills --skill d3-design
npx skills add D3OXY/skills --skill create-pr
npx skills add D3OXY/skills --skill ubiquitous-language
```

Install **several** skills in one command:

```sh
npx skills add D3OXY/skills --skill d3-design --skill create-pr --skill ubiquitous-language
```

Install **all** skills from this repository (non-interactive):

```sh
npx skills add D3OXY/skills --all --yes
```

Forks: substitute your GitHub user or org for `D3OXY`. You can also install from a **subpath** when your host supports it (see [Skills CLI](https://github.com/vercel-labs/skills) docs for URL formats).

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
  ubiquitous-language/
    SKILL.md
LICENSE
README.md
```

Each skill’s **`SKILL.md`** includes YAML frontmatter (`name`, `description`) used for discovery and activation.

## GitHub “About” description (suggested)

Use this or shorten it in the repository **About** field:

> Multi-skill agent pack: **d3-design** (UI / frontend philosophy + optional cinematic glass aesthetic) and **create-pr** (PR titles, bodies, and review checklist). Install: `npx skills add D3OXY/skills`.

## Clone

```sh
git clone https://github.com/D3OXY/skills.git
```

If you still have a local remote pointing at the old `d3-design` name:

```sh
git remote set-url origin https://github.com/D3OXY/skills.git
```

GitHub redirects `D3OXY/d3-design` to `D3OXY/skills` after a rename, but updating `origin` avoids confusion.

## Forking and customization

Skills are meant to be **forked**. Adjust copy, checklists, or tokens to match your team; keep `name` in frontmatter aligned with the folder name if you rely on `--skill` installs.

## License

MIT — see [LICENSE](LICENSE).

## Author

[D3OXY](https://github.com/D3OXY)
