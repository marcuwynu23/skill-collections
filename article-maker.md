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

## AGENTS.md content (per-agent, stored here)
- Agent: Article-Maker
- Scope: `src/content/articles/**`
- Task: Generate article markdown files
- Convention: Match existing article files exactly (bold H1 title, date, table of contents, numbered sections, `---` dividers, Conclusion/References/Related Articles/Keywords at end)
- Output: One markdown file per article in a category subfolder