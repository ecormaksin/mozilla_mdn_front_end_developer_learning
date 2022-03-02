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
