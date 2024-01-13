# HTMLに関するメモ

## [ハイパーリンク](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)

- リンクの追加情報を含める場合は、`title` 属性を使う。ただし、マウスを当てている時しかツール チップとして表示されないので、重要な情報は通常のテキストにする。[link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#adding_supporting_information_with_the_title_attribute)

    <details><summary>例</summary><div>

    ```html
    <p>
      I'm creating a link to
      <a
        href="https://www.mozilla.org/en-US/"
        title="The best place to find more information about Mozilla's
              mission and how to contribute">the Mozilla homepage</a>.
    </p>
    ```

    </div></details></br>

- ファイルをダウンロードさせる場合は、 `download` 属性にデフォルトのファイル名を指定する。[link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#use_the_download_attribute_when_linking_to_a_download)

    <details><summary>例</summary><div>

    ```html
    <a
      href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=en-US"
      download="firefox-latest-64bit-installer.exe">
      Download Latest Firefox for Windows (64-bit) (English, US)
    </a>
    ```

    </div></details></br>

- 宛先を指定した状態でメール アプリを開く場合は、`<a>` タグで `href="mailto:<宛先のメール アドレス>"` を指定する。 [link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#email_links)

    <details><summary>例</summary><div>

    ```html
    <a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
    ```

    </div></details>

  - `<宛先のメール アドレス>` は任意。カンマ区切りで複数指定できる。
  - `mailto:` では、宛先だけでなく件名・CC・BCC・本文なども指定できる。[link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#specifying_details)
    - URLのクエリ パラメーターの指定と同じ方式
      - 各項目はURLエンコードする。
      - 不可視文字を含めない。（タブ・キャリッジ リターン・改行）
      - スペースは `%20` でエスケープする。
      - メール アドレスの後ろに `?` を付加する。
      - 各項目は `&` で区切る。

      <details><summary>例</summary><div>

      ```html
      <a
        href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&subject=The%20subject%20of%20the%20email&body=The%20body%20of%20the%20email">
        Send mail with cc, bcc, subject and body
      </a>
      ```

      </div></details></br>

## [定義リスト（Description list）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#description_lists)

- `<dl><dt>定義対象の用語(description term)</dt><dd>定義の説明(description definition)</dd><!-- 定義の個数分のdt, ddの組。dtに対してddは複数記述できる。 --></dl>`/

## [引用符（Quotations）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#quotations)

- ブロック クォーテーション（block quotation）
  - `<blockquote cite="{引用元のURL}">{引用内容}</blockqote>`

- インライン クォーテーション（inline quotation）
  - `<q cite="{引用元のURL}">{引用内容}</q>`

- 各タグの`cite`属性は意味的な機能しかないので、実際の引用元はタイトルなどを`<a href="{引用元のURL}"><cite>{引用元のサイト名など}</cite></a>`でマークアップする。

## [略語（Abbreviations）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#abbreviations)

- `<abbr title="{正式な名称・呼称など}">{対象の略語}</abbr>`
  - アクセシビリティのために、ページ内の最初に記述する箇所で、平文で正式な用語も併記する。

- `<acronym></acronym>`は廃止されたので使わない。

## [連絡先の詳細のマーク アップ（Marking up contact details）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#marking_up_contact_details)

- `<address>{連絡先の詳細（<p>~</p>, <ul>~</ul>などの構造を埋め込める）}</address>`
- ページの作成者やページの所有者（企業のホームページの場合の企業）などの問い合わせ先をマークアップするために使うもので、ページ内に記述するあらゆる連絡先をマークアップするために使うものではない。

## [上付き文字と下付き文字（Superscript and subscript）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#superscript_and_subscript)

- `<sup></sup>`
- `<sub></sub>`

## [コンピューター コードの表現（Representing computer code）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#representing_computer_code)

- `<code></code>`: 汎用的なコンピューター コードの断片
- `<pre></pre>`: 空白文字がそのままレンダリングされる
- `<var></var>`: 変数名
- `<kbd></kbd>`: キーボード入力
- `<samp></samp>`: コンピューター プログラムの出力

## [日時のマークアップ（Marking up times and dates）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#marking_up_times_and_dates)

- `<time datetime="{コンピューターが認識可能な形式での日時}">{人間が読む形式での日時（テキスト情報のみ）}</time>`

## [内容を構成するためのHTML（HTML for structuring content）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure#html_for_structuring_content)

- ヘッダー: `<header></header>`
- ナビゲーション バー: `<nav></nav>`
- 主要な内容: `<main></main>`
  - ページ内で1つだけ。`<body></body>`の直下に記述する。
  - この中に、`<article></article>`, `<section></section>`, `<div></div>`を複数組み合わせて構成する。
    - `<article>`: ページ内の他の内容がなくても、それだけで意味を成す内容のかたまりを囲む。
    - `<section>`: `<article>`と似ているけれども、1つの機能を構成する複数の部品をグループ化する。（記事のヘッドラインや要約など）
- サイドバー: `<aside></aside>`
  - `<main></main>`内にしばしば記述される
  - ページの内容に間接的に関係する情報を提供するために使う。（用語集、ページ作成者の経歴、関連リンクなど）
- フッター: `<footer></footer>`

## [意味論的ではないタグ（Non-semantic wrappers）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure#non-semantic_wrappers)

内容をグループ化する時に、意味的に適切なタグがない時や、意味を持たせたくない時は、`<div></div>`(ブロック要素)／`<span></span>`(インライン要素)を使う。`class`属性で識別可能なクラス名を記述することが推奨される。

## [改行と水平の罫線（Line breaks and horizontal rules）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure#line_breaks_and_horizontal_rules)

- `<br />`
- `<hr />`

## [HTMLの検証（HTML validation）](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML#html_validation)

[Markup Validation Service](https://validator.w3.org/) を使う。

## [画像](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML#how_do_we_put_an_image_on_a_webpage)

- `<img>`タグを使う。
  - void element（終了タグがない、子要素を持たない）
  - 属性
    - `src`: 画像ファイルのパス(絶対パス／相対パス)
    - `alt`  代替の文字。
      - 画像が表示されない状況だったり、ネットワーク回線が遅く画像の読み込みが遅いときに使われる。
      - 検索エンジンでも使われる。
      - 背景画像やWebページに十分な説明がある場合は「`alt=""`」で設定する。
    - 画像のサイズに関する属性も指定した方が良い。
      - 実際の画像サイズと違う数値を指定すると画像が歪んだりするので、画像ファイルのサイズを適切に指定する。画像のサイズを本当に変更する必要がある場合は、CSSを使う方が良い。
      - `width`
      - `height`

- 検索エンジンは画像ファイル名を取得して、SEOに含める。そのため、画像ファイル名は説明的なものにした方がよい。

- `src`属性に絶対パスでURLを指定することもできるが推奨されない。HTMLのソースコードと同じサイトに画像ファイルも配置するか、CDNを使う方が良い。

- **他サイトに掲載されている画像のURLを許可なく、自分のWebページへ埋め込んではいけない。** そのような行為は"hotlinking"(直リンク)と呼ばれる。全般的に非倫理的とみなされる。また、自分のページへ誰かがアクセスした時に、リンク先の画像へアクセスするための帯域コストを誰かが払っていることになる。また、リンク先の画像が削除されたり別の画像に置き換わったりする可能性があり、自分では制御できない。
  - 掲載する画像は、以下のいずれかである必要がある。
    - 自分が所有している。
    - 画像の所有者から明文化された許可を得ている。
    - 公有の画像であることを証明できる。

- `<img>`や`<video>`タグは、**replaced element**と呼ばれることがある。この理由は、要素の中身が外部のリソース(画像や映像)によって規定されるから。

- 画像のタイトル情報を付与するには、`<figure>` `<figcaption>` を使う。これらのタグは、複数の画像を1つのまとまりとしてタイトルを付与したい場合や、コード スニペット、音声、映像、数式、表などにも使える。
  - 例

    ```html
    <figure>
        <img />
        <figcaption>
          画像のタイトル
        </figcaption>
    </figure>
    ```

### [CSSを使った背景画像](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML#css_background_images)

- 例: すべての段落に背景画像を表示する場合

  ```css
  p {
    background-image: url("images/dinosaur.jpg");
  }
  ```

- HTML画像とCSS画像の使い分け
  - Webページの内容に関係がある場合: HTML画像
  - ただの装飾の場合: CSS画像
