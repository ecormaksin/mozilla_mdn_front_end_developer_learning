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
