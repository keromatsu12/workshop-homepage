# workshop-homepage

AIにコーディング規約を守らせながらホームページを開発するワークショップ用のリポジトリです。

## ワークショップの概要

このリポジトリでは **GitHub Copilot（AI）** が、あらかじめ定義されたコーディング規約（スキルファイル）に従ってホームページを開発します。  
「AIに指示するだけで、規約に沿ったコードが生成される」という体験を通じて、AIとの協働開発の流れを学ぶことを目的としています。

---

## プロジェクト構成

```
homepage/
├── index.html       # メインページ
├── css/
│   └── style.css    # スタイルシート（BEM記法）
├── js/
│   └── main.js      # JavaScriptファイル
└── img/             # 画像ファイル
```

---

## 規約（スキルファイル）

AIが参照するコーディング規約は `.github/skills/` 配下にスキルファイルとして定義されています。  
AIはタスクの内容に応じて、自動的に対応するスキルを読み込んで実装を行います。

| スキル名 | 概要 |
| :--- | :--- |
| `html-structure-guide` | HTMLのセマンティクス・アクセシビリティ・クラス名適用ルール |
| `css-bem-guide` | CSS の BEM（Block, Element, Modifier）命名規則 |
| `git-version-control-guide` | Gitflow・Conventional Commit によるバージョン管理 |

---

## AIへの指示の流れ

### Step 1 — 実装（implementation エージェント）

チャットのエージェントを **`implementation_agent`**（`.github/agents/implementation.agent.md`）に切り替えて、タスクを日本語で指示します。

```
ヘッダーコンポーネントを実装して
```

エージェントは HTML 構造化規約・CSS BEM 記法ガイドラインなどのスキルを自動で参照し、規約に沿ったコードを生成・ファイルに書き込みます。

---

### Step 2 — レビュー（review エージェント）

**新しいチャットを開き**、エージェントを **`review_agent`**（`.github/agents/review.agent.md`）に切り替えてレビューを依頼します。

```
実装した変更をレビューして
```

エージェントはローカルの差分を取得し、HTML・CSS BEM・Git の各規約への準拠状況をチェックして Markdown 形式でレポートを出力します。

---

### Step 3 — PR 原稿生成（pr_template_generator プロンプト）

レビューが完了したら、`.github/prompts/pr_template_generator.prompt.md` を使って PR の本文を生成します。  
コマンドパレット（`Ctrl+Shift+P`）から **「プロンプトの実行」** を選択するか、チャットで以下のように指示します。

```
/pr_template_generator
```

現在の `git diff` をもとに、所定のテンプレート（概要・変更点・テスト・申し送り事項）に沿った PR 本文が日本語で生成されます。

---

## 開発ルール

- ブランチ戦略：**Gitflow**（`main` / `develop` / `feature/*`）
- コミット形式：**Conventional Commit**（例：`feat: ヒーローセクションを追加`）
- CSS命名：**BEM記法**（例：`.card__title--highlighted`）
