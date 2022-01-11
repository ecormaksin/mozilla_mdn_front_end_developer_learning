# HTML学習メモ

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
    - `<title>`要素
    - CSSへのリンク
    - カスタムfaviconへのリンク
    - その他のメタデータ: `<meta>`要素。データを説明するデータ
      - ページの著者
      - web検索時に表示されるキーワードやページの説明
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


## ヘッダー（`<head>`要素）

### `<meta>`要素

- 多くの機能はすでに使われていない。
  - `<meta name="keywords" content="~">`は、検索エンジンで別の単語で検索された時に、関連する単語で検索に該当させる目的で設計されていたが、スパム発信者がとにかく検索にヒットするように関係のない単語まで大量に設定する手法を採るので、検索エンジンでは無視されるようになった。

#### `<meta>`要素の属性

- `name`: メタ要素の種類を表す。
- `content`: メタ要素の実際の内容。

- ページの著者やページの説明を定義するのに役立つ。
  - 例

  ```html
  <meta name="author" content="Chris Mills">
  <meta name="description" content="The MDN Web Docs Learning Area aims to provide complete beginners to the Web with all they need to know to get started with developing web sites and applications.">
  ```

  - ページの作者を設定しておくと、誰がそのページを作ったのかが分かり、質問がある場合に問い合わせることができる。
  - ページの内容に関連するキーワードを含んだ説明を設定しておくと、検索エンジンで関連するページにより該当する可能性が高くなる。（[Search Engine Optimization / SEO / 検索エンジン最適化](https://developer.mozilla.org/en-US/docs/Glossary/SEO)）

#### 他の種類のメタデータ

- [Open Graph Data](https://ogp.me/): Facebook(Meta)がwebサイトにより情報量を持たせられるメタデータを提供するために開発した。
  - 例: Facebookで表示した時に、画像と説明がリンクと合わせて表示される。

    ```html
    <meta property="og:image" content="https://developer.mozilla.org/static/img/opengraph-logo.png">
    <meta property="og:description" content="The Mozilla Developer Network (MDN) provides and HTML5 Apps. It also documents Mozilla products, like Firefox OS.">
    <meta property="og:title" content="Mozilla Developer Network">
    ```

- [Twitter Cards](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards): Twitterが開発したOpen Graph Dataと同様のもの。
  - 例

    ```html
    <meta name="twitter:title" content="Mozilla Developer Network">
    ```

### サイトにカスタム アイコンを追加する

- **favicon**: "favorite icon" / 「お気に入りアイコン」の短縮形。
  - 次のような箇所で表示される。
    - 「お気に入り」や「ブックマーク」のリスト
    - ページを表示した時のタブ
  - faviconをサイトに追加する方法
    1. サイトのインデックス ページと同じディレクトリーに、`.ico`形式で画像を保存する。ほとんどのブラウザーは、`.gif`や`.png`のような形式もサポートするが、ICO形式はIE6までサポートする。
    2. `<head>`要素内にfavicon画像を参照する行を追加する。
       - 例

        ```html
        <link rel="icon" href="favicon.ico" type="image/x-icon">
        ```

  - 上記の他にも多くのアイコンの種類がある。
    - 例: MDN Web Docsのホームページのソース コード

      ```html
      <!-- 高解像度のRetinaディスプレイを搭載した第3世代のiPad -->
      <link rel="apple-touch-icon-precomposed" sizes="144x144" href="https://developer.mozilla.org/static/img/favicon144.png">
      <!-- 高解像度のRetinaディスプレイを搭載したiPhone -->
      <link rel="apple-touch-icon-precomposed" sizes="114x114" href="https://developer.mozilla.org/static/img/favicon114.png">
      <!-- 第1・第2世代のiPad -->
      <link rel="apple-touch-icon-precomposed" sizes="72x72" href="https://developer.mozilla.org/static/img/favicon72.png">
      <!-- Retinaディスプレイ非搭載のiPhone, iPod TouchとAndroid 2.1以上のデバイス -->
      <link rel="apple-touch-icon-precomposed" href="https://developer.mozilla.org/static/img/favicon57.png">
      <!-- 基本のアイコン -->
      <link rel="icon" href="https://developer.mozilla.org/static/img/favicon32.png">
      ```

  - **備考**: セキュリティ向上のために、サイトでContent Security Policy (CSP)を使う場合、アイコンにもポリシーが適用される。もしfaviconが読み込まれない問題が発生する場合、[Content-Security-Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy)ヘッダーの[`img-src`ディレクティブ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/img-src)がfaviconへのアクセスを妨げていないか確認する。

### HTMLへのCSSとJavaScriptの適用

- CSS

  ```html
  <head>
    <!-- 他の要素があれば記述 -->
    <link rel="stylesheet" hrefs="my-css-file.css">
    <!-- 他の要素があれば記述 -->
  </head>
  ```

- JavaScript

  ```html
  <head>
    <!-- 他の要素があれば記述 -->
    <script src="my-js-file.js" defer></script>
    <!--                        | -->
    <!--                        HTMLの解析後にJavaScriptを読み込むための指示 -->
    <!-- 他の要素があれば記述 -->
  </head>
  ```

  - `defer`キーワードを指定することで、JavaScriptがまだ描画されていない要素へアクセスしようとしてエラーが発生することを防止できる。JavaScriptの読み込みを制御する方法はたくさんあるが、`defer`を指定する方法が一番簡単。（他の方法は、[Script loading strategies](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_is_JavaScript#script_loading_strategies)を参照。）
  - `<script></script>`タグの中にスクリプトを記述することもできる。

### ドキュメントの第1言語の設定

```html
<html lang="en-US">
```

- 設定することで、検索エンジンによって、より効果的にインデックスが生成される。  
- スクリーン リーダーを使っている視覚障害者によって役に立つ。（例: "six"はフランス語にも英語にもある単語だが、発音は違う。）
- ページ内のセクションに別の言語を指定することもできる。
  - 例

    ```html
    <p>Japanese example: <span lang="ja">ご飯が熱い。</span>.</p>
    ```
  - 言語のコードは[ISO 639-1](https://en.wikipedia.org/wiki/ISO_639-1)標準で定義されている。
  -詳細は[Language tags in HTML and XML](https://www.w3.org/International/articles/language-tags/)を参照。
