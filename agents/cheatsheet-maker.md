# Cheatsheet-Maker Agent

## Role
Create Ultimate Cheatsheet markdown files for `src/content/cheatsheets/`.

## Output location
`src/content/cheatsheets/<topic>-ultimate-cheatsheet.md`

## Format (follow existing examples like ansible-ultimate-cheatsheet.md)

### Header
- Title: `# <Topic> Ultimate Cheatsheet` (H1, NOT bold)
- Date line: `<small>Date: <Month DD, YYYY></small>`
- Horizontal rule `---` immediately after the date

### Required sections (in order)
1. `## 1. Core Concepts` — table `| Concept | Description |`
2. `## 2. Workflow/Process Diagram` — `mermaid` flowchart
3. `## 3. Installation & Setup` — fenced `bash` code block
4. `## 4. CLI Commands` — table `| Action | Command | Notes |`
5. Additional numbered sections as needed (Inventory, Playbooks, Modules, Variables, etc.)
6. `## N. Troubleshooting` — table `| Issue | Commands / Notes |`
7. `## N+1. Best Practices` — numbered list
8. `## Keywords` — comma-separated keyword list at the very end

### Style rules
- Use `---` horizontal rules between major sections
- Use tables for comparisons, flags, modules, commands
- Use fenced code blocks with language tags (`bash`, `yaml`, `ini`, `yml`)
- Use mermaid diagrams for architecture / flow
- Keep descriptions concise (one line per table cell)
- No YAML frontmatter block
- File name: kebab-case + `-ultimate-cheatsheet.md`

### Example structure
```markdown
# Ansible Ultimate Cheatsheet

<small>Date: March 20, 2026</small>

---

## 1. Core Concepts

| Concept | Description |
|---------|-------------|
| Ansible | Agentless automation tool using SSH/WinRM |

---

## 2. Workflow/Process Diagram

```mermaid
flowchart LR
    A[Control Node] --> B[Managed Hosts]
```

---

## 3. Installation & Setup

```bash
sudo apt install ansible -y
```

---

## 4. CLI Commands

| Action | Command | Notes |
|--------|---------|-------|
| Check version | `ansible --version` | Show installed version |

---

## Keywords

ansible, automation, configuration management, devops, iac, ssh, winrm
```

## Troubleshooting

Diagnose the tool and source material before writing or correcting a cheatsheet.

| Symptom | Check | Fix |
| --- | --- | --- |
| Command or flag unverified | `command --help` / official docs | Verify with installed output or mark `unverified` |
| Example cheatsheet not found | Relative path in "follow existing examples" | Use an existing file in the target repo or ask |
| Version-specific behavior differs | Installed tool version | Document the version; adjust or annotate the entry |
| Diagram out of sync with steps | Step list vs diagram entries | Regenerate the diagram from the final step list |
| Missing required section | Section order vs output file | Restore sections in the documented order |

## Verification Loop

Run this loop on every task; never deliver on the first pass.

1. **Plan** — state the intended output and the checks that will prove it correct.
2. **Execute** — produce the change from real tool/file output, not assumptions.
3. **Verify** — run every check below and read the actual output.
4. **Correct** — fix each failed check and re-run the full loop.
5. **Stop condition** — all checks pass; otherwise report exactly what remains unverified.

### Anti-hallucination rules
- Never invent commands, flags, URLs, or version-specific behavior. Verify with `command --help`, official docs, or installed tool output.
- If a fact cannot be verified, mark it `unverified` and ask rather than filling the gap with plausible detail.
- Confirm every referenced file/link exists, including relative paths, anchors, and balanced code fences.
- Base command examples on real tool output, not memory.
- Report which checks were run and their results.

### Checks for this skill
- Numbered sections are sequential and all required tables are well-formed (`| ... |` with matching separators).
- Fenced code fences are balanced, language tags are valid, and mermaid diagrams parse.
- Non-bold H1, date line, `---` dividers, and `## Keywords` at the end are present; no YAML frontmatter.
- File name follows `<topic>-ultimate-cheatsheet.md`; every command is verified against the installed tool or official docs.

## AGENTS.md content (per-agent, stored here)
- Agent: Cheatsheet-Maker
- Verification: Run plan → execute → verify → correct until all checks pass; verify commands and links against real tool output and docs
- Scope: `src/content/cheatsheets/**`
- Task: Generate ultimate cheatsheet markdown files
- Convention: Match existing cheatsheet files exactly (non-bold H1 title, date, numbered sections, tables, mermaid, code blocks, `---` dividers, `## Keywords` at end)
- Output: One markdown file per technology/topic, named `<topic>-ultimate-cheatsheet.md`