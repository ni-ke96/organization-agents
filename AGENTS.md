# AGENTS.md

This repository manages structured project knowledge extracted from raw memos.
Agents operate **exclusively via slash commands** and must follow this specification.

---

# 1. Repository Structure

- `memos/`
  - Raw memo files.
  - **Agents must NEVER modify or delete these files.**

- `projects/<project-id>/`
  - Contains structured project documentation.
  - Created from templates and updated incrementally.

- `glossary/`
  - Contains shared dictionaries for technical terms and ubiquitous language.

- `templates/`
  - Source templates for project files and glossary files.
  - **Agents must NEVER modify these files.**
  - Used only when generating new project or glossary files.

- `AGENTS.md`
  - This ruleset.

---

# 2. Goals for Agents

When a slash command is executed:

1. Read memos from `memos/` only (read-only).
2. Extract structured information.
3. Classify into:
   - Project facts / decisions / requirements → `notes.md`
   - Issues / unclear points → `issues.md`
   - Technical terms → `glossary/technical-terms.md`
   - Domain terms → `glossary/ubiquitous-language.md`
4. Update files incrementally without breaking their format.
5. Use templates when files are missing.

All generated documentation must be in **Japanese**.

---

# 3. Template Initialization

When creating a new project:

- `projects/<project-id>/overview.md`  
  → `templates/project-overview.md`
- `projects/<project-id>/notes.md`  
  → `templates/project-notes.md`
- `projects/<project-id>/issues.md`  
  → `templates/project-issues.md`

When glossary files do not exist:

- `glossary/technical-terms.md`  
  → templates/glossary-technical-terms.md
- `glossary/ubiquitous-language.md`  
  → templates/glossary-ubiquitous-language.md

**Templates themselves must not be edited.**

---

# 4. Memo → Project Conversion Rules

## 4.1 Identify project
- Detect which project(s) the memo belongs to based on content or explicit mentions.

## 4.2 Write facts, decisions, requirements → notes.md
- Append under:
```

## From memos/<file-name>

````
- Summaries only（原文コピーしない）

Example:
- [決定事項]
- [仕様メモ]
- [検討中]

## 4.3 Write unclear or pending topics → issues.md
Each issue must include:

| Field | Description |
|-------|-------------|
| ID | Project-local sequential ID（A-01, A-02…） |
| Status | open / in-progress / closed |
| Type | clarification / requirement-clarification / ubiquitous-language-meaning |
| Summary | 概要 |
| Source memo | memos/<file> |
| Note | 任意 |

## 4.4 Technical terms → glossary/technical-terms.md
- No duplicates.
- Extend existing definitions where appropriate.

## 4.5 Ubiquitous language terms → glossary/ubiquitous-language.md
- Mark ambiguous definitions as `tentative`.
- When `tentative` → 必ず対応する issue を作成。

## 4.6 Updating overview.md（限定的）
Only update overview.md when the memo clearly contains:
- プロジェクトの目的変更 / スコープ変更  
- 主要ステークホルダーの追加・変更  
- 大きなマイルストーンの決定  
- 主要な概念の定義（用語メモとして格納されていたものが確立した場合）

**日々の詳細な仕様・メモは絶対に overview に書かない。**

---

# 5. Output Rules

- **Do NOT wrap full file contents in ``` code fences**  
unless user explicitly asks to “show the file content”.
- Always apply real file edits to the workspace.
- Maintain existing heading structure and valid Markdown tables.
- Increment issue IDs correctly.

---

# 6. Guardrails

- Never modify `memos/` or `templates/`.
- Prefer incremental edits.
- Never delete glossary entries unless explicitly requested.
- When classification is uncertain, add short Japanese notes.

---

# 7. Slash-like Commands

These commands are the primary way users interact with the agent.

---

## /organize-memo <path>

Example:
````

/organize-memo memos/2025-11-10-pj-taskflow.md

````

Behavior:
- Read the specified memo.
- Detect related project(s).
- Initialize missing project files from templates.
- Update:
  - projects/<project-id>/overview.md（必要時のみ）
  - projects/<project-id>/notes.md
  - projects/<project-id>/issues.md
  - glossary/technical-terms.md
  - glossary/ubiquitous-language.md
- **Never print entire file blocks inside ``` fences.**
- Apply diffs directly to workspace.
- Ask for confirmation before finalizing changes.

---

## /scan-memos

- Process ALL memos under `memos/`.
- Perform the same transformation as `/organize-memo`.
- Group diffs by project.
- Ask for confirmation before applying.

---

## /new-project <project-id>

- Create new `projects/<project-id>/` directory.
- Initialize:
  - overview.md
  - notes.md
  - issues.md
- Do not overwrite existing files.

---

## /refresh-glossary

- Scan all project notes.
- Update glossary files.
- Do not delete existing entries unless explicitly told.

---

Agents must respond **only** to these slash commands.

---

# End of AGENTS.md
