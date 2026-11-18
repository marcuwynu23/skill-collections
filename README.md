<div align="center">

  <p><strong> Reusable AI agent instruction files for content generation and expert guidance.</strong></p>

<a href="#overview"><img src="https://img.shields.io/badge/agents-10-informational" alt="Agents: 10"></a>
<img src="https://img.shields.io/badge/hosting-GitHub%20Pages-222" alt="Hosting: GitHub Pages">
<img src="https://img.shields.io/badge/config-AGENTS.md-2ea44f" alt="Config: AGENTS.md">

</div>

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Available Skills](#available-skills)
- [Quick Start](#quick-start)
  - [curl](#curl)
  - [PowerShell irm](#powershell-irm)
  - [wget](#wget)
  - [cp (local copy)](#cp-local-copy)
- [How It Works](#how-it-works)
- [Hosting on GitHub Pages](#hosting-on-github-pages)
- [Guidelines](#guidelines)
- [References](#references)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This repository is a practical collection of reusable agent instruction files for AI coding tools. Each `.md` file defines an agent's role, output location, formatting conventions, and style rules. Copy or download the file you need into your target project and rename it to `AGENTS.md` so the instructions are applied automatically.

## What You Will Find

- Content generators for articles, case studies, and cheatsheets
- Expert agents for infrastructure, Git, and programming languages
- A consistent per-agent format with role, scope, conventions, and output rules
- A `## AGENTS.md content (per-agent, stored here)` block inside every skill
- Files hosted on GitHub Pages so they can be fetched directly with `curl`, `irm`, or `wget`

## Architecture

```mermaid
flowchart TD
    A[Skill Collections] --> B[Content Generators]
    A --> C[Expert Agents]

    B --> B1[article-maker]
    B --> B2[case-study-maker]
    B --> B3[cheatsheet-maker]

    C --> C1[ansible, terraform, crossplane]
    C --> C2[git, issue-ticket-gh]
    C --> C3[golang, nodejs-ts]

    B1 & B2 & B3 & C1 & C2 & C3 --> D[AGENTS.md]
    D --> E[AI coding tool applies instructions]

    style A fill:#2ea44f,color:#fff
    style D fill:#0db7ed,color:#fff
```

## Available Skills

### Content Generators

- [article-maker](./article-maker.md)
- [case-study-maker](./case-study-maker.md)
- [cheatsheet-maker](./cheatsheet-maker.md)

### Infrastructure Experts

- [ansible-expert](./ansible-expert.md)
- [terraform-expert](./terraform-expert.md)
- [crossplane-expert](./crossplane-expert.md)

### Workflow Experts

- [git-expert](./git-expert.md) — Conventional Commits, branching, PR hygiene
- [issue-ticket-gh-expert](./issue-ticket-gh-expert.md) — create GitHub issues with `gh`

### Language Experts

- [golang-expert](./golang-expert.md)
- [nodejs-ts-expert](./nodejs-ts-expert.md)

## Quick Start

Every method below fetches a skill file and writes it as `AGENTS.md` in your target project. Replace `<USERNAME>`, `<REPO>`, and the skill filename with your own values. Examples use `ansible-expert.md`; swap in any filename from [Available Skills](#available-skills).

### curl

macOS / Linux / Git Bash / WSL:

```bash
BASE_URL="https://<USERNAME>.github.io/<REPO>"
SKILL="ansible-expert.md"

curl -fsSL "$BASE_URL/$SKILL" -o /path/to/your/project/AGENTS.md
```

One-liner from your project root:

```bash
curl -fsSL https://<USERNAME>.github.io/<REPO>/ansible-expert.md -o AGENTS.md
```

Flags: `-f` fail on HTTP errors, `-s` silent, `-S` still show errors, `-L` follow redirects, `-o <file>` write to `AGENTS.md`.

### PowerShell irm

`irm` is an alias for `Invoke-RestMethod`:

```powershell
$baseUrl = "https://<USERNAME>.github.io/<REPO>"
$skill   = "ansible-expert.md"

irm "$baseUrl/$skill" -OutFile "C:\path\to\your\project\AGENTS.md"
```

One-liner from your project root:

```powershell
irm "https://<USERNAME>.github.io/<REPO>/ansible-expert.md" -OutFile AGENTS.md
```

`iwr` / `Invoke-WebRequest` works identically:

```powershell
iwr "https://<USERNAME>.github.io/<REPO>/git-expert.md" -OutFile AGENTS.md
```

> In PowerShell, `wget` and `curl` are aliases for `Invoke-WebRequest`, so GNU-style flags do not work there — use `irm ... -OutFile`.

### wget

Classic `wget` (Linux / macOS via Homebrew / MSYS2):

```bash
BASE_URL="https://<USERNAME>.github.io/<REPO>"
SKILL="ansible-expert.md"

wget -qO /path/to/your/project/AGENTS.md "$BASE_URL/$SKILL"
```

One-liner from your project root:

```bash
wget -qO AGENTS.md https://<USERNAME>.github.io/<REPO>/ansible-expert.md
```

Flags: `-q` quiet, `-O <file>` write to `AGENTS.md`.

### cp (local copy)

After cloning this repository locally:

```bash
git clone https://github.com/<USERNAME>/<REPO>.git
cp skill-collections/ansible-expert.md /path/to/your/project/AGENTS.md
```

Or from inside this folder:

```bash
cp article-maker.md /path/to/your/project/AGENTS.md
cp git-expert.md     /path/to/your/project/AGENTS.md
```

> Any of these methods overwrites an existing `AGENTS.md` in the destination. Back it up first if you need to keep it.

## How It Works

1. Each skill file contains a role, output path, required sections, and style rules.
2. Fetching or copying it into `AGENTS.md` makes those instructions active in the destination project.
3. The agent then generates content or follows the conventions exactly as described in the file.
4. To switch skills, simply replace `AGENTS.md` with a different file.

## Hosting on GitHub Pages

1. Push this folder to a GitHub repository (e.g. `skill-collections`).
2. In the repo, go to **Settings → Pages** and set the source to the branch containing these files (usually `main` / `/root`).
3. Add an empty `.nojekyll` file at the repo root so the `.md` files are served as raw text instead of being processed by Jekyll:

   ```bash
   touch .nojekyll
   git add .nojekyll && git commit -m "chore: disable Jekyll for raw markdown" && git push
   ```

4. Your files are then available at:

   ```text
   https://<USERNAME>.github.io/<REPO>/<file>.md
   ```

   Replace `<USERNAME>` with your GitHub username and `<REPO>` with the repository name. For a user/org site (`<USERNAME>.github.io`) there is no `/<REPO>` path segment.

## Guidelines

### Best Practices

1. **Pick one skill per `AGENTS.md`** — replace the file to switch agents; do not merge multiple skill files.
2. **Back up existing instructions** before overwriting `AGENTS.md`.
3. **Use an absolute output path** in `curl`/`irm`/`wget` commands, or run from the project root.
4. **Keep the source files unchanged** — customize the copied `AGENTS.md` in your project instead.
5. **Verify the download** after fetching:
   ```bash
   head -n 5 AGENTS.md
   ```

### Troubleshooting

| Problem | Solution |
|---|---|
| `404` from `curl`/`irm`/`wget` | Check `<USERNAME>`, `<REPO>`, filename, and that Pages is enabled |
| HTML returned instead of markdown | Add `.nojekyll` at the repo root and wait for the Pages rebuild |
| `curl: command not found` | Use PowerShell `irm`, `wget`, or install curl |
| PowerShell `wget` flags fail | It is an `Invoke-WebRequest` alias — use `irm ... -OutFile` |
| `AGENTS.md` not applied | Ensure the file is at the project root with the exact name |

### Useful Commands

```bash
curl -fsSL "$BASE_URL/$SKILL" -o AGENTS.md              # curl
irm "$baseUrl/$skill" -OutFile AGENTS.md                 # PowerShell
wget -qO AGENTS.md "$BASE_URL/$SKILL"                    # wget
cp article-maker.md /path/to/your/project/AGENTS.md      # local copy
head -n 5 AGENTS.md                                      # verify
```

## References

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [curl Documentation](https://curl.se/docs/)
- [GNU wget Manual](https://www.gnu.org/software/wget/manual/)
- [PowerShell Invoke-RestMethod](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-restmethod)

## Contributing

Contributions are welcome. To add or improve a skill, open a pull request with a short description of the agent's role, scope, and conventions, and include an example of its expected output.

## License

This project is licensed under the MIT License.
