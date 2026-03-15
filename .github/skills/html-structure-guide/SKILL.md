---
name: html-structure-guide
description: HTML構造化規約に関するガイドライン。セマンティクス、アクセシビリティ、クラス名の適用ルールを定めます。
---

# **I. HTML 構造化規約**

HTMLの適切な構造化、セマンティクス、アクセシビリティ、およびクラス名の適用ルールに関するガイドラインです。

## When to use this skill

- HTMLファイルを作成、または修正する際。
- セマンティックなHTML要素（header, main, footerなど）や見出し構造を定義する際。
- BEM記法に基づくクラス名をHTML要素に適用する際。
- スクリプト（JS）ファイルや外部リソース（CSS等）を読み込む設定を行う際。

## How to use it

### **1\. ドキュメント構造**

- **DOCTYPE/HTML:** \<\!DOCTYPE html\> で始まり、言語属性 (lang="ja") を含む \<html\> 要素を使用します。
- **メタタグ:** charset (UTF-8) およびビューポート設定 (width=device-width, initial-scale=1.0) を必ず含めます。
- **OGP (Open Graph Protocol):** 外部 SNS での共有時に適切なプレビューが表示されるよう、OGP タグを head 内に設定します。画像 URL やファビコンはプロジェクト内のパスを使用します。
- **外部リソース:** CSS/フォントなどの \<link\> 要素は、パフォーマンスのため \<head\> 内に配置し、非同期で読み込む設定（例: display=swap）を推奨します。

### **2\. セマンティクスとアクセシビリティ**

- **セマンティック要素:** ページの主要な構造には、header、main、footer、section、nav などのセマンティック HTML5 要素を適切に使用します。
- **見出し構造:** h1 から h6 の見出しレベルを階層的に正しく使用し、スキップしないようにします。
- **代替テキスト:** 全ての \<img\> 要素には、意味のある alt 属性を必ず記述します。
- **ARIA:** 動的なコンテンツやカスタムコンポーネント（例: ハンバーガーメニュー）には、必要に応じて適切な ARIA 属性（aria-expanded など）を付与します。

### **3\. クラス名**

- **BEM 統一:** クラス名は、全て **II. CSS BEM 記法ガイドライン** に従います。HTML タグ名や ID は CSS セレクタとして直接使用することを避け、BEM クラスを主要なスタイリングのターゲットとします。
- **属性の利用:** JavaScript からの制御やアニメーション制御が必要な場合は、data-animation や data-parallax のように data- 属性を利用し、BEM クラスと役割を分離します。

### **4\. スクリプトの読み込み**

- **JS ファイル:** 外部 JavaScript ファイルの読み込みは、HTML の解析をブロックしないよう、終了タグ \</body\> の直前に配置し、可能な限り defer 属性または async 属性を使用します。
  - 例: \<script src="dist/bundle.js" defer\>\</script\>
