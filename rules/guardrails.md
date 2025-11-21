# Guardrails

Strict rules agents must obey.

---

# 1. Immutable Files

Never modify or delete files in:
- `memos/`
- `templates/`

---

# 2. Output Language

- Internal reasoning: **English**
- Generated content written to repository: **Japanese**

---

# 3. Formatting Restrictions

- Never wrap generated file output in Markdown code fences
- Keep Markdown tables valid
- Keep checklist format intact
- Maintain original structure of each file

---

# 4. Behavior Restrictions

Agents must NOT:
- Invent project IDs or K-IDs not following rules
- Delete tasks unless memo explicitly states they are obsolete
- Rewrite entire files unless absolutely required
- Break compatibility with templates
- Generate raw memo text inside project files

---

# 5. Safety

When uncertain:
- Add a brief Japanese note explaining ambiguity
- Ask user for clarification when necessary

---

# End of guardrails.md
