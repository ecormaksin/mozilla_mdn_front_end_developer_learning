# 学習メモ

## 要素

```text
<p>My cat is very grumpy</p>
|  |                    |
|  |                    Cloging tag / 終了タグ
|  Content / 内容
Opening tag / 開始タグ

※上記全体: Element / 要素
```

### 全般

- 大文字・小文字は区別されない。ただし、一貫性・可読性のために、小文字で書くのがベスト プラクティス。
- 要素は入れ子にできる。

### ブロック要素とインライン要素

- HTML5では要素の分類が再定義されている。（[参照先](https://html.spec.whatwg.org/multipage/indices.html#element-content-categories)）新しい定義はブロック要素やインライン要素よりも理解が難しいので、MDNでは2つの用語で説明している。
- 「ブロック」「インライン」という用語を、[CSSのボックスの型](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model#types_of_css_boxes)と混同してはいけない。CSSでdisplayの属性を変更しても、HTML上のブロック／インライン自体が変更されるわけではない。HTML5でブロック／インラインが廃止されたのは、CSS側との混同を避けるため。

- [ブロック要素](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)
  - ページ上の視覚的なブロックを形成する。
  - 新しい行に表示される。
  - ページ上の構造的な要素。
  - 見出し・段落・リスト・ナビゲーション メニュー・フッターなどを表す。
  - インライン要素の中にはネストできない。
  - 他のブロック要素の中にはネストできる。

- [インライン要素](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)
  - ブロック要素内に配置する。
  - ドキュメントの内容の小さい部分のみを囲む。（段落全体や複数の内容を囲むことはない。）
  - 新しい行には表示されない。

### 個別のタグ（MDNの学習ページで例示されたもの）

- 段落: `<p></p>`
- イタリック体: `<em></em>`
- 強調: `<strong></strong>`
