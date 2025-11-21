# Slash Command Rules

Agents must support these commands:

---

# 1. /organize-memo <path>

Processes a single memo:
- Identify target project(s)
- Update:
  - overview.md (high-level only)
  - notes.md
  - issues.md
  - tasks.md
  - glossary files
  - knowledge cards
  - knowledge index
- Ask user for confirmation before applying changes

---

# 2. /scan-memos

Process all memos under `memos/`:
- Apply same logic as `/organize-memo`
- Group changes by project
- Ask for confirmation before applying

---

# 3. /new-project <project-id>

Creates new project directory and initializes:
- overview.md
- notes.md
- issues.md
- tasks.md
- procedures/

---

# 4. /refresh-glossary

Rebuild glossary entries by scanning notes files.

---

# 5. /sync-tasks-from-memo <path>

Only task extraction and task updates.  
No modification to notes/issues/glossary/knowledge.

---

# 6. /generate-procedure <project-id> <topic>

Uses hybrid RAG knowledge to generate a new procedure file.

---

# End of commands.md
