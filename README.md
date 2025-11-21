# 📘 README — 自動化プロジェクト情報管理システム

このリポジトリは、**メモを起点にプロジェクト情報を自動整理・構造化するための基盤**です。
GitHub Copilot を用いて次のような文書・ナレッジを自動生成・更新します。

* プロジェクトノート（notes）
* 課題（issues）
* タスク（tasks）
* 用語集（glossary）
* ナレッジカード（knowledge cards）
* 手順書（procedures）

また、本リポジトリ全体の動作ルールは **rules ディレクトリ**に分割されており、
**AGENTS.md が全体のインデックス**になっています。

---

# 🧪 利用可能な Slash コマンド

| コマンド                                       | 説明                |
| ------------------------------------------ | ----------------- |
| `/organize-memo <path>`                    | 指定したメモを読み取り、PJに反映 |
| `/scan-memos`                              | memos/ 全メモを一括整理   |
| `/new-project <project-id>`                | 初期プロジェクト一式を生成     |
| `/refresh-glossary`                        | 用語集を再生成           |
| `/sync-tasks-from-memo <path>`             | タスクだけ更新           |
| `/generate-procedure <project-id> <topic>` | ナレッジに基づき手順書生成     |

---

# 🚀 機能一覧

## 1. 📝 メモ整理（/organize-memo）

`memos/` に保存したメモから、以下の情報を自動抽出します：

* 決定事項、仕様メモ、検討事項 → `projects/<project-id>/notes.md`
* 論点・不明点・定義曖昧 → `issues.md`
* 行動項目（アクション） → `tasks.md`
* 技術用語 → `glossary/technical-terms.md`
* ドメイン用語（ユビキタス言語） → `glossary/ubiquitous-language.md`
* 再利用可能な知見 → `organization/knowledge` のナレッジカード

### 特徴

* **元メモは絶対に変更しません。**
* 文章そのままコピーせず、必ず「要点の日本語まとめ」を生成します。
* 1つのメモが複数プロジェクトにまたがる場合にも対応します。

---

## 2. 🧩 ナレッジカード（RAG-like ファイルデータベース）

メモから抽出した「再利用できる知識」は **1カード1ファイルの形式**で保存されます。

保存先：

```
organization/knowledge/common/
organization/knowledge/<project-id>/
```

管理のポイント：

* K-ID（K-TASKFLOW-001 のような連番）で管理
* すべて **日本語** で記載
* 関連ナレッジ（他カード）とのリンクが追加される
* `knowledge/index.md` にメタ情報で一覧化される

これにより、**RAG 的な知識再利用が極めて簡単**になります。

---

## 3. ✔ タスク管理（シンプルチェックリスト）

`projects/<project-id>/tasks.md` は、
表ではなく **チェックボックス型の軽量タスクリスト**として管理されます。

例：

```
- [ ] T-TASKFLOW-001 タスク作成画面のワイヤーフレームを作成する（担当: 山田 / 期限: ）
- [x] T-TASKFLOW-002 ワークロード案を3パターン作成する（担当: 佐藤 / 期限: 2025-11-12）
```

### 特徴

* 完了したタスクは **削除せず [x] にして残す**
* 担当者・期限の抽出にも対応
* プロジェクト管理ツールとの併用がしやすい

---

## 4. 📚 用語集（Glossary）

2種類の用語集を管理します：

* **技術用語**
  `glossary/technical-terms.md`
* **ユビキタス言語**（ドメイン用語）
  `glossary/ubiquitous-language.md`

ユビキタス言語で意味が曖昧なものは `tentative` となり、
**自動的に issue 化**されます。

---

## 5. 🧪 手順書生成（/generate-procedure）

任意のテーマで手順書を生成できます。

流れ：

1. テーマから関連ナレッジカード候補を自動抽出
2. ユーザーに「使用するカード一覧」を提示
3. 確定したカードのみを読み込み
4. ハイブリッドRAG（軽量）で内容を生成
5. `projects/<project-id>/procedures/<slug>.md` に保存

生成される手順書は完全に **日本語** です。

---

## 6. 🧭 ルール体系（rules/ ディレクトリ）

本システムのコアとなる仕様・ルールはすべて **英語**で `rules/` に分割されています。

構成：

```
rules/
 ├ structure.md          → リポジトリ構造規約
 ├ templates.md          → テンプレ使用ルール
 ├ memo-organization.md  → メモ整理仕様
 ├ glossary.md           → 用語集管理
 ├ knowledge.md          → ナレッジカード仕様
 ├ tasks.md              → タスク管理
 ├ procedures.md         → 手順書生成
 ├ commands.md           → Slashコマンド定義
 └ guardrails.md         → 禁止事項・安全対策
```

全体像のインデックスが `AGENTS.md` です。

---

# 🧠 内部処理の原則

* **思考（推論）は英語**
* **出力（生成されるファイル内容）は日本語**
* 基本的に「追加・更新」を行い、全置換は避ける
* memos/ と templates/ は絶対に変更しない

---

# 📂 典型的なディレクトリ構造（抜粋）

```
memos/
projects/
  └ taskflow/
      ├ overview.md
      ├ notes.md
      ├ issues.md
      ├ tasks.md
      └ procedures/
glossary/
organization/
  └ knowledge/
      ├ index.md
      ├ common/
      └ taskflow/
templates/
rules/
AGENTS.md
README.md
```

---

# 🏁 はじめ方

1. `memos/` にメモファイルを置く
2. Copilot Chat で

   ```
   /organize-memo memos/2025-11-10-taskflow.md
   ```

   を実行
3. 内容確認後、差分を accept
4. 必要に応じて手順書やタスクを更新する
5. `knowledge/` が育つほど、手順書品質が向上します

---

# 🎉 この仕組みで実現すること

* メモを取るだけで、**必要な情報が全部自動的に反映される**
* ナレッジが自然に貯まり **自分専用RAGデータベースになる**
* 手順書は **使い回し可能な高品質なドキュメント**に育つ
* コマンドベースで運用できるので **GitHub Copilot と相性抜群**
