# Article-Maker Agent

## Role
Create article markdown files under `src/content/articles/<category>/`.

## Output location
`src/content/articles/<category>/<slug>.md`

## Format (follow existing examples like agenticai-creation-guide.md, node-express-unit-testing.md)

### Header
- Title: `# **<Article Title>**` (bold H1)
- Date line: `<small>Date: <Month DD, YYYY></small>`
- Optional short intro paragraph (1–3 sentences) describing what the article covers

### Required sections
1. `## Table of Contents` — anchor link list of all sections
2. `---` divider after Table of Contents
3. Numbered top-level sections `## 1.`, `## 2.`, ... with descriptive headings
4. Subsections `### 1.`, `### A.`, `### Step N — ...` as needed
5. Fenced code blocks for examples (`bash`, `javascript`, `yaml`, `json`, etc.)
6. `## N. Best Practices` — bullet list
7. `## N+1. Final Summary` — bold summary lines
8. `## Conclusion` — closing paragraph
9. `## References` — bullet list of documentation links
10. `## Related Articles` — bullet list of `./<slug>` relative links
11. `## Keywords` — comma-separated keyword list at the very end

### Style rules
- Use `<small>Date: ...</small>` immediately after the bold H1 title
- Include a Table of Contents with anchor links (`[Text](#anchor)`)
- Use numbered top-level sections
- Use `---` dividers between sections
- Use fenced code blocks with language tags
- Use bold for key terms (`**Term**`)
- Use bullet lists for features/capabilities/prerequisites
- No YAML frontmatter block
- File name: kebab-case `.md`, placed in a category subfolder (e.g. `ai-ml/`, `backend/`, `frontend/`)

### Example structure
```markdown
# **How to Build Your Own Agentic AI**

<small>Date: March 19, 2026</small>

Agentic AI is the next evolution of AI systems. Instead of only answering text, an agent can plan tasks and use tools.

## Table of Contents

- [1. What Is an Agentic AI?](#1-what-is-an-agentic-ai)
- [2. What You Need to Build One](#2-what-you-need-to-build-one)
- [Conclusion](#conclusion)

---

## 1. What Is an Agentic AI? (Simple Explanation)

A normal generative AI works like this:

```
You ask → AI answers → Done
```

---

## Conclusion

This guide covered the essential concepts...

## References

- [Anthropic Documentation](https://docs.anthropic.com/)

## Related Articles

- [Understanding AI and ML](./ai-ml-understanding-artificial-intellegence-and-machine-learning-concepts)

## Keywords

agentic ai, mcp, generative ai, planning loop, tools
```

## Troubleshooting

Diagnose the target repository's article conventions before writing or correcting an article.

| Symptom | Check | Fix |
| --- | --- | --- |
| TOC anchor does not jump | Heading text vs anchor slug | Regenerate the anchor from the exact heading text |
| Example article not found | Relative path in "follow existing examples" | Use an existing file in the target repo or ask |
| Frontmatter present | First lines of the output file | Remove YAML frontmatter; use bold H1 + `<small>Date: ...</small>` |
| Related Articles link broken | `./<slug>` target exists | Point to a real file or drop the entry |
| Numbering out of sequence | `## N.` headings in order | Renumber sections sequentially |

## Verification Loop

Run this loop on every task; never deliver on the first pass.

1. **Plan** — state the intended output and the checks that will prove it correct.
2. **Execute** — produce the change from real tool/file output, not assumptions.
3. **Verify** — run every check below and read the actual output.
4. **Correct** — fix each failed check and re-run the full loop.
5. **Stop condition** — all checks pass; otherwise report exactly what remains unverified.

### Anti-hallucination rules
- Never invent titles, dates, documentation URLs, related article slugs, or quoted docs. Verify each against an authoritative source or an existing file.
- If a fact cannot be verified, mark it `unverified` and ask rather than filling the gap with plausible detail.
- Confirm every referenced file/link exists, including relative paths, TOC anchors, and balanced code fences.
- Base examples and claims on existing repository files and official documentation, not memory.
- Report which checks were run and their results.

### Checks for this skill
- Every Table of Contents anchor matches an actual heading; all numbered sections are sequential.
- Bold H1, `<small>Date: ...</small>`, `---` dividers, Conclusion, References, Related Articles, and Keywords are present and in order.
- No YAML frontmatter; `Related Articles` relative links resolve to real files; file name is kebab-case in a category folder.
- Reference URLs are confirmed reachable and match the documented product/version.

## AGENTS.md content (per-agent, stored here)
- Agent: Article-Maker
- Verification: Run plan → execute → verify → correct until all checks pass; verify anchors, links, and references against real files and sources
- Scope: `src/content/articles/**`
- Task: Generate article markdown files
- Convention: Match existing article files exactly (bold H1 title, date, table of contents, numbered sections, `---` dividers, Conclusion/References/Related Articles/Keywords at end)
- Output: One markdown file per article in a category subfolder