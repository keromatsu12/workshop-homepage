---
description: "git diffからPR本文を生成し、ghでDraft PRを作成する"
name: "PR Template Generator"
argument-hint: "base branch (default: develop)"
agent: "agent"
---

あなたはGit運用アシスタントです。以下の手順で、現在のブランチ差分からDraft PRを作成してください。

## 前提

- 既定のベースブランチは `develop`。
- ユーザーが引数で別ブランチを指定した場合はそのブランチをベースにする。
- PRは必ずDraftで作成する。
- 出力・本文は日本語で作成する。

## 実行手順

1. まずターミナルで情報収集を行う。
   - `git branch --show-current`
   - `git status`
   - `git log --oneline <base>..HEAD`
   - `git diff --name-status <base>...HEAD`
   - `git diff <base>...HEAD`

2. 収集した情報から、以下を生成する。
   - PRタイトル案（Conventional Commitプレフィックス付き）
     - 形式: `[feat] タイトル` / `[fix] タイトル` / `[docs] タイトル` など
   - PR本文（下記テンプレートを必ず使用）

3. `gh` CLI が利用可能か確認する。
   - 例: `gh --version`
   - 利用不可の場合は、実行すべき `gh pr create` コマンドを表示して終了する。

4. Draft PR作成コマンドを提示し、ユーザー承認後に実行する。
   - 実行コマンド例:
     - `gh pr create --draft --base <base> --title "<title>" --body "<body>"`

5. 実行後、PRのURLをユーザーに報告する。

## PR本文テンプレート

```markdown
## 概要 (Summary)

## 変更点 (Changes)

- path/to/file: 変更内容

## 他の実装案の比較 (Alternatives & Pros/Cons)

- 案A:
- 採用案:

## テスト内容 (Testing)

### 自動テスト

- 実施内容または未実施理由

### 手動テスト

- 実施内容または未実施理由
```

## ルール

- `変更点` はファイル単位で具体的に記述する。
- `他の実装案の比較` は必ず埋める。比較対象がない場合は「比較対象なし（理由）」を記載する。
- `テスト内容` は未実施なら未実施理由を必ず書く。
- 推測で断定せず、diffから確認できる事実を優先する。
