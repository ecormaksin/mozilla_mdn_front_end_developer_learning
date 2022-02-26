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
