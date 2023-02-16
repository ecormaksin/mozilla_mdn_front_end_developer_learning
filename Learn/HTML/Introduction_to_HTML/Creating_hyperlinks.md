# Creating hyperlinks / ハイパーリンクの作成

## Anatomy of a link / リンクの構造

- `<a>`要素と`href`属性（ **ハイパーテキスト参照(Hypertext Reference)** または **ターゲット(target)** として知られている）を使う。
  - 例

    ```html
    <p>I'm creating a link to
    <a href="https://www.mozilla.org/en-US/">the Mozilla homepage</a>.
    </p>
    ```

### Adding supporting information with the title attribute / title属性で補足情報を追加する

- `title`属性
  - リンクに関する追加の情報を含む。
    - ページがどのような種類の情報を含んでいるか。
  - ポインターを当てた時にツールチップのようにタイトルが表示される。
    - キーボードやタッチパネルで操作する場合は表示されない。
      そのため、重要な情報の場合は通常のテキストに配置したりして、すべてのユーザーがアクセス可能な状態にする必要がある。
  - 例

    ```html
    <p>I'm creating a link to
    <a href="https://www.mozilla.org/en-US/"
      title="The best place to find more information about Mozilla's
      mission and how to contribute">the Mozilla homepage</a>.
    </p>
    ```

### Block level links / ブロック要素のリンク

- ブロック要素も含め、おおよそどのようなものでもリンクに埋め込むことができる。
  - 例

    ```html
    <a href="https://www.mozilla.org/en-US/">
      <img src="mozilla-image.png" alt="mozilla logo that links to the mozilla homepage">
    </a>
    ```

## A quick primer on URLs and paths / URLとパスに関する簡単な入門

- URL: Uniform Resource Locator

- ファイル システム上のパスの扱い

  - 例

    ```text

    |
    | contacts.html
    | index.html
    |
    |-- pdfs
    |   `-- project-brief.pdf
    |
    `-- projects
        `-- index.html

    ```

  - 同じディレクトリー: ファイル名のみで参照可能。
    - ルートの`index.html`から見た`contacts.html`

      ```html
      <p>Want to contact a specific staff member?
      Find details on our <a href="contacts.html">contacts page</a>.</p>
      ```

  - サブディレクトリー内へ階層を下げる: `フォルダー/ファイル`
    - ルートの`index.html`から見た、`projects`ディレクトリー内の`index.html`

      ```html
      <p>Visit my <a href="projects/index.html">project homepage</a>.</p>
      ```

  - 親ディレクトリーへ階層を上げる: `../`
    - `projects`ディレクトリー内の`index.html`から見た、`pdfs`ディレクトリー内の`project-brief.pdf`

      ```html
      <p>A link to my <a href="../pdfs/project-brief.pdf">project brief</a>.</p>
      ```

### Document fragments / ドキュメントの断片

- HTMLドキュメントの特定箇所（ **ドキュメントの断片(document fragment)** として知られている）へリンクすることもできる。
  - リンク先の要素に`id`属性を割り当てる。

    ```html
    <h2 id="Mailing_address">Mailing address</h2>
    ```

  - URLの後ろにハッシュ記号(`#`)と`id`属性を記載する。

    ```html
    <p>Want to write us a letter? Use our <a href="contacts.html#Mailing_address">mailing address</a>.</p>
    ```

  - 同じファイル内のドキュメントの断片へリンクする時は、`#id`のみ

    ```html
    <p>The <a href="#Mailing_address">company mailing address</a> can be found at the bottom of this page.</p>
    ```

### Absolute versus relative URLs / 絶対 vs 相対 URL

- **絶対URL(absolute URL)**
- **相対URL(relative URL)**

- 絶対URL
  - プロトコル（protocol）とドメイン名（domain name）を含むweb上の絶対的な位置によって定義される。
  - 使われる場所に関係なく常に同じ場所を指す。

- 相対URL
  - リンク元のファイルの場所（パス上の階層）を移動すると、参照できていたリンク先を参照できなくなるので、注意が必要。

## Link best practices / リンクのベスト プラクティス

### Use clear link wording / 明確なリンクの表現を使う

ページを閲覧している人の状況やツールの選択に関わらず、すべての人にとってリンクを _アクセス可能_ にする必要がある。

- スクリーン リーダーの利用者は、ページ内のリンクからリンクへジャンプしたり、ページの内容とは別にリンクを読むことを好む。
  → ページ内リンクを整備する。
- 検索エンジンは、対象ファイルにインデックスを付けるために、リンクのテキストを使う。そのため、何がリンクされているかを効果的に説明するために、リンクのテキストにキーワードを含めるのは良い考え。
- 視覚的なページ閲覧者は、すべての言葉を読むよりもむしろ、ページをサッと見る（スキミングする）。そして、リンクのようにページ内の目立つ箇所に目を向けやすい。説明がしっかりしているリンクのテキストは役に立つだと感じられる。

- 例
  - 良いリンク テキスト: `Download Firefox`
  - 悪いリンク テキスト: `Click here`

- 他のコツ
  - リンク テキストの中でURLを繰り返さない。
    - 見た目が良くない。スクリーン リーダーが1文字ずつ読み上げるので分かりづらい。
  - リンク テキストの中で"リンク"や"～へのリンク"と書かない。
    - ノイズになってしまうため。スクリーン リーダーはリンクがあることを教えてくれる。視覚的には違う色で下線が付加されているのでリンクだと分かる。（このリンクのスタイルについて、利用者は慣れているので、通常は崩すべきではない。）
  - リンク テキストをできるだけ短くする。長いとスクリーン リーダーがリンク テキスト全体を解析する必要があるため。
  - 同じテキストでリンク先が異なるケースを必要最小限にする。スクリーン リーダーの利用者に混乱を招いてしまうため。

#### Linking to non-HTML resources - leave clear signposts / HTMLではないリソースへリンクする - 分かりやすい案内をつける

以下のようなリソースへリンクする時、混乱を減らすために明確な表現を追加する。

- ダウンロードが発生するファイル（pdfやWord文書）: ファイルの種類とサイズ（低速な環境で予期しないダウンロードが発生しないようにするため。）
- ストリーミングが発生するファイル（映像や音声）: 開かれる形式(現在のページが遷移するのか、新しいタブ・ウィンドウで開かれるのか)とリソースの品質（HDなど）
- その他、予期しない挙動が発生しうるもの（ポップアップ画面を開く、Flashムービーを読み込む等）
  - 例
    - 遅い帯域速度の時にリンクをクリックして、大容量ファイルのダウンロードが予期せず始まってしまう。
    - Flash playerをまだインストールしていない状態でリンクをクリックして、Flashを要求するページへ突然飛ばされてしまう。

良いリンクの例

```html
<p><a href="https://www.example.com/large-report.pdf">
  Download the sales report (PDF, 10MB)
</a></p>

<p><a href="https://www.example.com/video-stream/" target="_blank">
  Watch the video (stream opens in separate tab, HD quality)
</a></p>

<p><a href="https://www.example.com/car-game">
  Play the car game (requires Flash)
</a></p>
```

#### Use the download attribute when linking to a download / ダウンロード対象をリンクする時に「download」属性を使う

例

```html
<a
  href="">
</a>
```
