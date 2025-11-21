# Template Usage Rules

This document defines how agents should use the templates under `templates/`.

---

# 1. Template Directory Policy

- Templates are stored under:  
  `templates/`
- **Agents must NEVER modify or delete template files.**

Templates serve as the canonical source for initializing:
- Project overview
- Project notes
- Project issues
- Project tasks
- Glossary files
- Knowledge cards
- Procedure files
- Knowledge index

---

# 2. Project Template Initialization

When a project directory is referenced or created, initialize missing files:

1. `projects/<project-id>/overview.md`  
   ← from `templates/project-overview.md`

2. `projects/<project-id>/notes.md`  
   ← from `templates/project-notes.md`

3. `projects/<project-id>/issues.md`  
   ← from `templates/project-issues.md`

4. `projects/<project-id>/tasks.md`  
   ← from `templates/project-tasks.md`

5. `projects/<project-id>/procedures/`  
   ← create empty directory if missing

---

# 3. Glossary Template Initialization

If glossary files do not exist:

1. `glossary/technical-terms.md`  
   ← from `templates/glossary-technical-terms.md`

2. `glossary/ubiquitous-language.md`  
   ← from `templates/glossary-ubiquitous-language.md`

---

# 4. Knowledge Base Templates

Knowledge system files must follow templates:

- Common knowledge card  
  ← `templates/knowledge-card-common.md`

- Project-specific knowledge card  
  ← `templates/knowledge-card-project.md`

- Knowledge index  
  ← `templates/knowledge-index.md`

---

# 5. Procedure Template

All generated procedure files must be based on:

`templates/project-procedure.md`

---

# End of templates.md
