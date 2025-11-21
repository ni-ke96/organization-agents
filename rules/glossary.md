# Glossary Management Rules

This document defines how to maintain glossary files.

---

# 1. Files

- `glossary/technical-terms.md`
- `glossary/ubiquitous-language.md`

Files contain **Japanese** entries.

---

# 2. Technical Terms

Columns:
- Term
- Category
- Definition (JA)
- First seen in

Rules:
- Add an entry when a term first appears in memos or notes
- Update definition when new information is found
- Avoid duplicates
- Keep definitions concise and in Japanese

---

# 3. Ubiquitous Language

Columns:
- Term
- Definition
- Domain
- Status (`tentative`, `confirmed`)
- Related project
- First seen in

Rules:
- Register any domain-specific term that appears in the memo
- If its meaning is unclear → set `Status = tentative`
- For tentative items, also create an issue (`ubiquitous-language-meaning`)
- When meaning is established later, update status to `confirmed`

---

# End of glossary.md
