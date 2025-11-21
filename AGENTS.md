# AGENTS.md

This repository defines an automated system for transforming raw memos into:

- structured project documentation  
- issues  
- tasks  
- glossary entries  
- reusable knowledge cards (RAG-like)  
- procedures based on knowledge cards  

To keep this file minimal and maintainable, **all operational rules are located under the `/rules` directory**.  
**Agents must follow all rule files exactly.**

All rule files are written in **English**.  
All generated repository content (notes, issues, tasks, knowledge cards, glossary entries, procedures) must be written in **Japanese**.  
Agents must perform internal reasoning in **English**.

---

# Rule Index

## 1. Repository Structure
Describes required directories, file placement, encoding rules, and general constraints.  
→ **[rules/structure.md](rules/structure.md)**

## 2. Template Usage Rules
Defines how templates must be used when initializing new project files, glossary, tasks, procedures, and knowledge cards.  
→ **[rules/templates.md](rules/templates.md)**

## 3. Memo Organization
Rules for processing memos via `/organize-memo` and `/scan-memos`.  
Extracts notes, issues, tasks, glossary entries, and knowledge.  
→ **[rules/memo-organization.md](rules/memo-organization.md)**

## 4. Glossary Management
Technical terms and ubiquitous language extraction and maintenance rules.  
→ **[rules/glossary.md](rules/glossary.md)**

## 5. Knowledge Card System (RAG)
Rules for generating, updating, and indexing reusable knowledge cards.  
→ **[rules/knowledge.md](rules/knowledge.md)**

## 6. Task Management (Lightweight Checklist)
Rules for extracting tasks from memos, updating them, and maintaining the checklist.  
→ **[rules/tasks.md](rules/tasks.md)**

## 7. Procedure Generation (Hybrid RAG)
Rules for `/generate-procedure`, card selection, hybrid RAG context, and procedure creation.  
→ **[rules/procedures.md](rules/procedures.md)**

## 8. Slash Command Definitions
Complete specification of all supported slash commands.  
→ **[rules/commands.md](rules/commands.md)**

## 9. Guardrails & Safety
Strict limitations to prevent corruption of repository data.  
→ **[rules/guardrails.md](rules/guardrails.md)**

---

# Agent Behavior Principles

1. **Internal reasoning MUST be performed in English.**  
2. **Generated output written into the repository MUST be in Japanese.**  
3. Agents must NEVER modify:  
   - `memos/`  
   - `templates/`  
4. All updates must follow Markdown formatting strictly.  
5. When uncertain, agents should note ambiguity (in Japanese) or ask the user for clarification.

---

# End of AGENTS.md
