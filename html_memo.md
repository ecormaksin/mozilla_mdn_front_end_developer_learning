# 学習メモ

## 要素

```text
<p class="editor-note">My cat is very grumpy</p>
|  |                   |                    |
|  |                   |                    Cloging tag / 終了タグ
|  |                   Content / 内容
|  Attributes / 属性
Opening tag / 開始タグ

※上記全体: Element / 要素
```

- 開始・終了のない単一のタグで構成される要素もある。（empty elements / void elements / 空の要素 ← 上記の構造に当てはめると、「内容」がないことから、そのように読んでいる？）

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
- 強調: `<strong></strong>` `<em></em>`
- リンク・アンカー（anchor）: `<a></a>`
  - `href`: リンク先のwebアドレス
    - 例: `href="https://www.mozilla.org/"`
  - `title`: リンク先ページの説明。カーソルを当てた時にツールチップとして表示される。
    - 例: `title="The Mozila homepage"`
  - `target`: リンクを表示するための閲覧状態を指定する。省略すると、現在のタブからリンク先ページへ遷移する。
    - 例: `target="_blank"` 新しいタブにリンク先のページを表示する。
- 画像: `<img src="<画像のパス>">`
- ドキュメントの表題: `<h1></h1>`

## 属性

- 要素の名前との間にスペースが必要
- 属性を複数指定する場合は、それぞれの間をスペースで区切る
- 属性名の後は`=`
- 属性値は引用符で囲む。
  - 省略することもできるが、問題が発生しやすいので、非推奨。
    - 例

      ```html
      <a href=https://www.mozilla.org/>fate website</a> <!-- OK -->

      <a href=https://www.mozilla.org/ title=The Mozilla homepage>favorite website</a>
      <!--                                   |   |       | -->
      <!--                                   |   |       真偽値と判断される -->
      <!--                                   |   真偽値と判断される -->
      <!--                                   Theだけがtitleの属性値と判断される -->
      ```

  - `'`と`"`のどちらを使うか。
    - スタイルの問題
    - 1つの属性値の開始と終了は同じ種類でなければならない。
    - 属性値の中に、属性値を囲んでいる引用符と同じ種類の引用符を設定することはできない。
      - 例

        ```html
        <a href="https://www.example.com" title="Isn't this fun?">A link to my example.</a><!-- OK -->

        <a href='https://www.example.com' title='Isn't this fun?'>A link to my example.</a><!-- NG -->

        <a href='https://www.example.com' title='Isn&apos;t this fun?'>A link to my example.</a><!-- OK -->
        ```

### 真偽属性 / Boolean attributes

- 値のない属性。
- ほとんどが名前と同じ値を持つ。
- 例
  - `disabled`  
    下の2つは同じ結果になる。  

    ```html
    <input type="text" disabled="disabled">
    <input type="text" disabled>
    ```

## HTMLドキュメントの構造

- `<!DOCTYPE html>`: doctype / ドキュメントの種類。
  - HTML(1991-1992)が未成熟だった時、doctypeはルールへのリンク機能を持つよう設計されていた。
    - ルール: 対象のwebページが良いHTMLと判定されるために従うべきルール
    - 例

      ```html
      <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
      ```

  - より最近では、doctypeは歴史的産物になり、正しく機能するために含める必要のあるだけの要素になった。
- `<html></html>`: ルート要素。ページ内の要素すべてを包含する。
- `<head></head>`: ヘッダー要素。ページ閲覧者には見せない内容を含めるためのコンテナーとして機能する。
  - head要素に含めるものの例
    - web検索時に表示されるキーワードやページの説明
    - CSS
    - 文字セットの定義など
- `<meta charset="utf-8">`: ページの文字セット。必ず設定する。
- `<title></title>`: ページのタイトル。ブラウザーのタブに表示される。ブックマークした時にも使われる。
- `<body></body>`: ページに表示するすべての内容（文字、画像、映像、ゲーム、再生可能な音声トラック、など）を含む。
- 空白は何個入力しても、単一のスペースとして描画される。

## 実体参照: HTML内の特殊文字

| 表示される文字 | HTML上の記述 |
| --- | --- |
| < | \&lt; |
| > | \&gt; |
| " | \&quot; |
| ' | \&apos; |
| & | \&amp; |

上記以外にも実体参照はあるが、文字エンコーディングをUTF-8に設定している限り、他の記号はそのまま描画される。

[すべてのリスト](https://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references)
