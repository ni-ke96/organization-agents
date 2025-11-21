# Memo Organization Rules

These rules define how agents extract structured information from memo files under `memos/`.

---

# 1. Input Constraints

- Only read from `memos/`
- Never modify files in `memos/`

Agents interpret memos using English internal reasoning and produce Japanese output files.

---

# 2. Project Identification

When reading a memo, determine its related project(s) using:
- Explicit project names / IDs
- Contextual hints
- Keywords found in memos

A memo may map to multiple projects.

---

# 3. Notes Extraction

Write extracted information to:

`projects/<project-id>/notes.md`

Rules:
- Use a section header:  
  `## From memos/<file-name>`
- Summaries only  
- No copying of raw sentences
- Use Japanese tags:  
  - `[決定事項]`  
  - `[仕様メモ]`  
  - `[検討中]`

---

# 4. Issue Extraction

Write issues to:

`projects/<project-id>/issues.md`

Issue fields (Japanese output):
- ID (project-local sequential)
- Status (`open`/`in-progress`/`closed`)
- Type (`clarification`, `requirement-clarification`, `ubiquitous-language-meaning`)
- Summary
- Source memo
- Note

---

# 5. Glossary Extraction

See glossary rules (rules/glossary.md).  
Agents must detect:
- Technical terms
- Ubiquitous language
- Unclear definitions → mark as `tentative` and create issues

---

# 6. Knowledge Extraction

See rules/knowledge.md.

Agents must extract reusable conceptual knowledge and convert it into knowledge cards.

---

# 7. Task Extraction

See rules/tasks.md.

---

# 8. Overview Updates

Update overview.md **only** for high-level project information:
- Purpose
- Scope boundaries
- Key stakeholders
- Milestones
- Core domain concepts

Do **not** write low-level memo content into the overview.

---

# End of memo-organization.md
