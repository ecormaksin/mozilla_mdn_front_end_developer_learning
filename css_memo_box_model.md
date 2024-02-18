# CSS ボックス モデルに関するメモ

※スタイルの適用に関するアルゴリズムとはまったく異なる内容なので、別ファイルにする。

[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)

- boxの分類
  - **blok box(boxes)**
  - **inline box(boxes)**

- boxは以下2つの **display type** を持つ。`display` 属性で指定する。
  - **inner display type**
  - **outer display type**

- outer display type
  - `display: block` の場合（`<h1>`, `<p>`などの初期状態）:
    - 新しい行に配置される。
    - `width`, `height` 属性が適用される。
    - padding, margin, borderの設定値によっては、他要素がboxからはみ出る可能性がある。
    - `width` が未指定の場合、対象要素が配置されているコンテナ内で横いっぱい(多くの場合100％)に広がる。
  - `display: inline` の場合（`<a>`, `<span>`, `<strong>`などの初期状態:
    - 新しい行には分かれない。
    - `width`, `height` 属性は適用されない。
    - 上下のpadding, margin, borderは適用されるが、他のinline boxがboxからはみ出るようなことは発生しない。
    - 左右のpadding, margin, borderも適用され、他のinline boxがboxからはみ出る可能性がある。

- boxの部品（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model#parts_of_a_box))
  - 下に記載されていくものほど外側になる。
  - content box: 中身、コンテンツが表示される領域。`inline-size`, `block-size`, `width`, `height`などの属性を使って大きさを指定する。
  - padding box: コンテンツの周りの余白。`padding`や関連する属性で指定する。
  - border box: `border`や関連する属性で指定する。
  - margin box: `margin`や関連する属性で指定する。

- Margin collapsing（余白の崩壊？）
  - 隣接するmargin(margin-bottom/margin-top, margin-right/margin-left)の設定値による表示の差異
  - 2つとも正の値の場合、大きい方が採用される。
    - 例
      - 上側の`margin-bottom: 50px;`、下側の`margin-top: 30px;`の場合、余白は50pxになる。）
  - 2つとも負の値の場合、小さい方が採用される。
  - 1つが負の値の場合、全体の合計から減算される。
