# Repository Structure Rules

This document defines the structural rules for all directories and files used by the automation agents.

---

# 1. Overview

The repository consists of these main areas:

- `memos/`  
  Raw memo files written by humans.  
  **Agents must NEVER modify or remove files in this directory.**

- `projects/<project-id>/`
  Structured project documentation, including:
  - `overview.md`
  - `notes.md`
  - `issues.md`
  - `tasks.md`
  - `procedures/<slug>.md`

- `glossary/`
  Shared terminology dictionaries:
  - `technical-terms.md`
  - `ubiquitous-language.md`

- `organization/knowledge/`
  File-based knowledge base (RAG-like system), containing:
  - `index.md`
  - `common/` → shared reusable knowledge cards  
  - `<project-id>/` → project-specific knowledge cards

- `templates/`
  All templates used for initialization.  
  **Agents must NEVER modify these files.**

- `rules/`
  This folder. Contains all operational rule documents.

- `AGENTS.md`
  Root-level index that links to all rule files.

---

# 2. File Encoding and Language Rules

- All rule files and templates must be written in **English**.
- All generated project documentation (notes, issues, tasks, glossary, knowledge cards, procedures) must be written in **Japanese**.
- Agents must think internally in **English**, but output Japanese when modifying repository content.

---

# 3. General Principles

- Use incremental updates rather than rewriting entire files.
- Maintain clean Markdown formatting at all times.
- Never break table structures or list formatting.
- Never generate fenced code blocks when writing to project files.
- Treat `memos/` and `templates/` as read-only sources of truth.

---

# End of structure.md
