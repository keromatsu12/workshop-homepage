---
name: css-bem-guide
description: CSS BEM記法ガイドライン。CSSの記述においてBEM（Block, Element, Modifier）記法を標準化します。
---

# **III. CSS BEM 記法ガイドライン**

このガイドラインは、CSS の記述において、BEM（Block, Element, Modifier）記法を標準化します。

## When to use this skill

- CSSファイルを作成、または修正する際。
- クラスの命名規則としてBEM（Block, Element, Modifier）を適用する際。
- スタイルガイド（`styleguide.html`）を更新する際。
- UIコンポーネントのスタイリングを行う際。

## How to use it

### **1\. BEM の命名規則**

#### **1.1. Block (ブロック)**

アプリケーションの独立した構成要素。再利用可能である必要があります。

- **名前:** 小文字の英単語をハイフン（-）で繋ぎます。（例: search-form, main-nav）
- **定義:**
  `/* ブロック全体を定義 */`
  `.card {`
  `display: flex;`
  `padding: 16px;`
  `border: 1px solid #ccc;`
  `}`

#### **1.2. Element (要素)**

ブロックを構成する部品。単独では意味を持たず、必ず親ブロックとセットで使用されます。

- **名前:** ブロック名にアンダースコアを 2 つ（\_\_）付けて繋ぎます。（例: card\_\_header, card\_\_image）
- **定義:**
  `/* カードの要素（タイトル）を定義 */`
  `.card__title {`
  `font-size: 1.5rem;`
  `margin-bottom: 8px;`
  `}`

#### **1.3. Modifier (修飾子)**

ブロックや要素の外観、状態、振る舞いを変更するためのフラグ。

- **名前:** ブロック名または要素名にハイフンを 2 つ（--）付けて繋ぎます。（例: card--large, card\_\_title--active）
- **定義:**
  `/* カードブロックのサイズを変更する修飾子 */`
  `.card--large {`
  `padding: 32px;`
  `max-width: 600px;`
  `}`

  `/* 要素の状態を変更する修飾子 */`
  `.card__button--disabled {`
  `opacity: 0.5;`
  `pointer-events: none;`
  `}`

### **2\. BEM の適用ルール**

#### **2.1. 状態の管理**

- **JavaScript による操作:** 修飾子クラスは、主に JavaScript から DOM に追加・削除され、状態の変化を表現するために使用します。
- **ブール値修飾子:** 単に状態を示す修飾子には、--is- プレフィックスを推奨します。（例: .nav\_\_item--is-selected）

#### **2.2. ネストの原則**

- **CSS のネスト:** メンテナンス性を高めるため、CSS においてはセレクタのネストを極力避けます。
- **HTML の構造:** HTML ではブロックと要素は親子関係を持ちますが、CSS クラス名にはその深さを反映させません。（例: card\_\_title は card\_\_header\_\_title とはしない）
