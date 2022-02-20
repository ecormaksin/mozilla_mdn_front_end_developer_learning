# What's in the head? Metadata in HTML / 頭の中には何がある？ HTML中のメタデータ

## What is the HTML head? / HTMLのheadとは何か？

- `<head>`要素の中身。
- ブラウザでページを読み込んだ時に表示されない。（`<body>`要素の中身は表示される。）
- ドキュメントに関する メタデータ（metadata）を含む役割を持つ。

## Adding a title / タイトルを追加する

- `<title>`要素。
- `<h1>`要素との違い
  - `<h1>`
    - ブラウザーで読み込まれた時、ページ上に表示される。
    - 一般的に、ページごとに1つ。
    - ページの内容のタイトル（物語のタイトル、ニュースの見出しなど）をマークアップするために使われる。
  - `<title>`
    - HTMLドキュメント全体のタイトルを表すメタデータ。（ドキュメントの中身に関するタイトルではない。）

## Metadata: the \<meta\> element / メタデータ: \<meta\>要素

- メタデータは、データを説明するデータ。

### Specifying your document's character encoding / ドキュメントの文字コードを指定する

```html
<meta charset="utf-8">
```

- 日本語を含むページで、文字コードに`ISO-8859-1`(Latin alphabet)を指定すると文字化けする。  
  Chromeのように自動的に文字コードを修正するブラウザーもあるが、`utf-8`を指定すべき。

### Adding an author and description / ページ作成者と説明を追加する

- 多くの`<meta>`要素は、`name`と`content`属性を含む。
  - `name`: メタ要素の種類。
  - `content`: メタ要素の実際の内容。

- ページの著者やページの説明を定義するのに役立つ。
  - 例

  ```html
  <meta name="author" content="Chris Mills">
  <meta name="description" content="The MDN Web Docs Learning Area aims to provide complete beginners to the Web with all they need to know to get started with developing web sites and applications.">
  ```

- ページ作成者を設定しておくと、誰がそのページを作ったのかが分かり、質問がある場合に問い合わせることができる。コンテンツ管理システムによっては、自動的にページ作成者の情報を抽出する機能を持っている。
- ページの内容に関連するキーワードを含んだ説明を設定しておくと、検索エンジンで関連するページにより該当する可能性が高くなる。（[Search Engine Optimization / SEO / 検索エンジン最適化](https://developer.mozilla.org/en-US/docs/Glossary/SEO)）

### Other types of metadata / 他の種類のメタデータ

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

### Adding custom icons to your site / サイトにカスタム アイコンを追加する

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

### Applying CSS and JavaScript to HTML / HTMLへのCSSとJavaScriptの適用

- CSS: `<link>`, JavaScript: `<script>`

- CSS

  ```html
  <head>
    <!-- 前後省略 -->
    <link rel="stylesheet" href="my-css-file.css">
    <!-- 前後省略 -->
  </head>
  ```

- JavaScript

  ```html
  <head>
    <!-- 前後省略 -->
    <script src="my-js-file.js" defer></script>
    <!--                        | -->
    <!--                        HTMLの解析後にJavaScriptを読み込むための指示 -->
    <!-- 前後省略 -->
  </head>
  ```

  - `defer`キーワードを指定することで、JavaScriptがまだ描画されていない要素へアクセスしようとしてエラーが発生することを防止できる。JavaScriptの読み込みを制御する方法はたくさんあるが、`defer`を指定する方法が一番簡単。（他の方法は、[Script loading strategies](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_is_JavaScript#script_loading_strategies)を参照。）
  - `<script></script>`タグの中にスクリプトを記述することもできる。

### Setting the primary language of the document / ドキュメントの第1言語の設定

```html
<html lang="en-US">
```

- 設定することで、検索エンジンによって、より効果的にインデックスが生成される。
  - 例
    - 言語を指定した時の検索結果に、正しく表示される。  
- スクリーン リーダーを使っている視覚障害者の助けになる。
  - 例
    - "six"はフランス語にも英語にもある単語だが、発音は違う。</br></br>

- ページ内のセクションに別の言語を指定することもできる。
  - 例

    ```html
    <p>Japanese example: <span lang="ja">ご飯が熱い。</span>.</p>
    ```

- 言語のコードは[ISO 639-1](https://en.wikipedia.org/wiki/ISO_639-1)標準で定義されている。
  - 詳細は[Language tags in HTML and XML](https://www.w3.org/International/articles/language-tags/)を参照。
