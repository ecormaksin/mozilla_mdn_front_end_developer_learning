# HTML text fundamentals / HTMLテキストの基礎

HTMLの主な仕事の1つは、開発者が意図した通りにブラウザーがHTMLドキュメントを表示できるように、テキストに構造を与えること。

## The basics: headings and paragraphs / 基礎: 見出しと段落

- 見出しは`<h[1-6]></h[1-6]>`で囲む。
  - `<h1>` `<h2>` `<h3>` `<h4>` `<h5>` `<h6>`の6段階
</br>
- 段落は`<p></p>`で囲む。
</br>
- 構造を作る時のベスト プラクティス
  - 1ページにつき、`<h1>`要素は1つ。
  - 階層構造上の正しい順序で見出しを使う。
    - 例: `<h3>`を`<h2>`より上位として扱ってはいけない。
  - 1ページに3レベルを超えて見出しを使わないようにする。1ページ内の階層が増えるようであれば、複数ページに分割する。

### Why do we need structure? / 構造が必要な理由

- webページを見ているユーザーは、関連した内容を見つけるために、最初はざっとページを眺める傾向がある。（1ページに留まっている時間はとても短い。[参照先URL](https://www.nngroup.com/articles/how-long-do-users-stay-on-web-pages/)）2, 3秒で有益な情報が見つからなかった場合、がっかりして他のページへ移動してしまう。
</br>
- ページをインデックス化している検索エンジンは、見出しの内容を、検索結果のランキングに影響を与える重要なキーワードとみなす。見出しがない場合、[SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO)(Search Engine Optimization / 検索エンジン最適化)
</br>
- 重度の視覚困難者はwebページを読む代わりに、「[スクリーン リーダー](https://en.wikipedia.org/wiki/Screen_reader)」で聴いている。スクリーン リーダーは、見出しを読み上げることで文書の概要を伝える。見出しが利用できない場合、スクリーン リーダーが文書全体を読み上げるのを聴くことになる。
</br>
- [CSS](https://developer.mozilla.org/en-US/docs/Glossary/CSS)で内容を整形したり、[JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript)でおもしろいことをするためには、関連する内容を包含した要素が必要になる。

### Why do we need semantics? / 意味合いが必要な理由

- 要素の役割を適切に表現するため。
- 検索エンジンやスクリーンリーダーなど、さまざまな方法で使われるため。
- CSSを使って`<span>`要素のテキストを見出しのような大きさに見せることはできるけれども、意味的には伝わらない。見出しなのであれば`<h1>`を使う必要がある。

## Lists / リスト

### Unordered / 順不同

  ```html
  <ul>
    <li>リスト項目1</li>
    <li>リスト項目2</li>
    <li>リスト項目3</li>
    <li>...</li>
  </ul>
  ```

### Ordered / 順序付きリスト

  ```html
  <ol>
    <li>リスト項目1</li>
    <li>リスト項目2</li>
    <li>リスト項目3</li>
    <li>...</li>
  </ol>
  ```

### Nesting lists / 入れ子のリスト

  ```html
  <ol>
    <li>順不同リスト項目1</li>
    <li>順不同リスト項目2</li>
    <li>順不同リスト項目3
      <ul>
        <li>サブ順不同リスト項目1</li>
        <li>サブ順不同リスト項目2</li>
      </ul>
    </li>
  </ol>
  ```

## Emphasis and importance / 強調と重要度

### Emphasis / 強調

- `<em></em>`
  - _イタリック体_ で表現される。
  - 単にイタリック体にしたい場合は、`<span>` + CSS or `<i>` を使う。

### Strong importance / 高い重要度

- `<strong></strong>`
  - **太字** で表現される。
  - 単に太字にしたい場合は、`<span>` + CSS or `<b>` を使う。
- 重要度と強調を合わせて使うこともできる。

  ```html
  <p>This liquid is <strong>highly toxic</strong> -
  if you drink it, <strong>you may <em>die</em></strong>.</p>
  ```

### Italic, bold, underline... / イタリック体、太字、下線…

- `<i>`, `<b>`, `<u>`
  - CSSのサポートが貧弱あるいはまったくなかった時の装飾目的で生まれた。
  - 意味合いを持たないので、 **表現用要素（presentational elements）** として知られている。

- HTML5で、これらの要素に新しくて、いくぶん混乱を招く意味的役割が再定義された。

- `<i>`: 外国語、分類上の名前 (taxonomic designation)、技術的な用語、思考
- `<b>`: キー ワード、プロダクト名、リード文
- `<u>`: 固有名詞 (proper name)、綴り誤り
  - 下線は、ハイパーリンクと認識される可能性がとても高い。そのため、web上ではハイパーリンクのみに下線をつけるのが最善。意味的に適切なら`<u>`を使えばよいが、CSSで見た目を変えた方が良い。
    - 例

      ```html
      <u style="text-decoration-line: underline; text-decoration-style: wavy;">spel</u>
      ```
