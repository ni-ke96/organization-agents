# Knowledge Card (RAG System) Rules

Defines how knowledge cards and the knowledge index operate.

---

# 1. Knowledge Card Types

### Common (global reuse)
Location:
`organization/knowledge/common/K-COMMON-XXX.md`

### Project-Specific
Location:
`organization/knowledge/<project-id>/K-<PROJECT-ID>-XXX.md`

Both types follow templates and must be generated in **Japanese**.

---

# 2. Card Structure

Each card contains:

- K-ID
- Title
- 種別 (type)
- タグ (tags)
- 関連用語 (related terms)
- 元メモ (source memo)
- 最終更新
- 内容
- 補足
- 関連ナレッジ (other K-IDs)

---

# 3. Knowledge Index

`organization/knowledge/index.md` contains metadata:

Columns:
- K-ID
- Title
- Tags
- Related Terms
- Project
- Path

Rules:
- Every new card must be added to the index
- Keep rows sorted by K-ID
- Do not embed full card content inside the index

---

# 4. Card Creation Rules

Create a new card when:
- Memo content reflects reusable knowledge
- A concept appears that spans multiple tasks or procedures
- A definition or rule emerges that should be preserved

Use common or project-specific card type appropriately.

---

# 5. Card Updates

When a memo adds nuance:
- Update the card contents
- Update related terms or tags
- Append related K-IDs if applicable

---

# End of knowledge.md
