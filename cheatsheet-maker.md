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

## AGENTS.md content (per-agent, stored here)
- Agent: Cheatsheet-Maker
- Scope: `src/content/cheatsheets/**`
- Task: Generate ultimate cheatsheet markdown files
- Convention: Match existing cheatsheet files exactly (non-bold H1 title, date, numbered sections, tables, mermaid, code blocks, `---` dividers, `## Keywords` at end)
- Output: One markdown file per technology/topic, named `<topic>-ultimate-cheatsheet.md`