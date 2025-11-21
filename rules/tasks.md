# Task Management Rules

Tasks are managed as lightweight checklists under:

`projects/<project-id>/tasks.md`

Tasks are written in **Japanese**, while internal reasoning is in English.

---

# 1. Task File Format

`tasks.md` must contain a section:

```

## タスクリスト

* [ ] T-<PROJECT-ID>-001 タスク内容（担当: X / 期限: YYYY-MM-DD）
* [x] T-<PROJECT-ID>-002 完了したタスク（担当: X / 期限: YYYY-MM-DD）

```

- One task per line
- Use GitHub-style checkboxes
- Do **not** use table format

---

# 2. New Task Extraction

A memo produces a new task if it includes:
- "ToDo", "やること", "アクションアイテム"
- Lines beginning with `TODO`, `対応`, `確認`, etc.
- Sentences ending with "〜する", "〜しておく"

The task format:

```

* [ ] T-<PROJECT-ID>-NNN タイトル（担当: X / 期限: YYYY-MM-DD）

```

Missing fields become:

```

（担当: / 期限: ）

```

---

# 3. Task Completion Updates

When a memo states:
- 完了した
- 対応済み
- 終わった
- DONE

The agent must update the relevant line:

```

* [x] T-<PROJECT-ID>-NNN タスク内容（担当: X / 期限: YYYY-MM-DD）

```

**Completed tasks are NOT removed.**

---

# 4. Task-ID Generation

Task IDs increment per project:

- T-PJID-001
- T-PJID-002
- ...

Algorithm:
1. Scan file for highest existing ID
2. Increment

---

# 5. Deletion Rules

Never delete tasks except when:
- Memo explicitly states the task is no longer needed
- Extraction was incorrect

---

# 6. Command Behavior

### /organize-memo  
Extracts and updates tasks alongside notes/issues/glossary/knowledge.

### /sync-tasks-from-memo  
Updates only tasks.

---

# End of tasks.md