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

1. **タスクを日本語で指示する**  
   例：「ヘッダーコンポーネントを実装して」「お問い合わせセクションを追加して」

2. **AIが規約を読み込む**  
   指示内容に応じたスキルファイルを自動で参照します。

3. **規約に沿ったコードが生成される**  
   HTMLのセマンティクス、CSSのBEM記法、コミットメッセージのConventional Commit形式など、すべての規約が自動的に適用されます。

---

## 開発ルール

- ブランチ戦略：**Gitflow**（`main` / `develop` / `feature/*`）
- コミット形式：**Conventional Commit**（例：`feat: ヒーローセクションを追加`）
- CSS命名：**BEM記法**（例：`.card__title--highlighted`）
