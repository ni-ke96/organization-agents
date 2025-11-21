# Procedure Generation Rules

Defines how procedures are generated using knowledge cards (hybrid RAG approach).

---

# 1. Procedure Location

Procedures are stored under:

`projects/<project-id>/procedures/<slug>.md`

Generated in **Japanese**, reasoning in English.

---

# 2. Candidate Knowledge Selection

Agents must:
1. Read `organization/knowledge/index.md`
2. Match cards based on:
   - Procedure topic/title
   - Relevant tags
   - Related terms
   - Project-specific knowledge
3. Present the candidate list to the user
4. Wait for confirmation before generating the procedure

---

# 3. Hybrid RAG Context

Once cards are selected:
- Load the individual card files
- Optionally construct a temporary merged “context view”
- Do **not** commit temporary files

Ground truth is always the individual card files.

---

# 4. Procedure Template Usage

Initial file from:

`templates/project-procedure.md`

Fields to populate:
- 目的
- 前提条件
- 参照ナレッジ（K-IDs）
- 手順（番号付き）
- 補足・注意点

---

# 5. Recording Used Knowledge

All referenced K-IDs must be listed in:

```

## 参照ナレッジ

```

Section must include:
- Common knowledge IDs
- Project-specific knowledge IDs

---

# 6. New Knowledge From Procedures

If procedure creation exposes reusable knowledge:
- Create a new knowledge card
- Insert into appropriate folder
- Add to index
- Link with `関連ナレッジ`

---

# End of procedures.md