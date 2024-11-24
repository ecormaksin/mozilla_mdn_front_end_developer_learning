# Web 開発関連メモ

HTML, CSS, JavaScript の複数領域にまたがる内容も含めて全部書く。

- 生成された内容（generated content）は、DOM に追加されない。そのため、スクリーン リーダーによっては不可視になる。（[リンク](https://developer.mozilla.org/en-US/docs/Learn/Forms/UI_pseudo-classes#using_generated_content_with_pseudo-classes)）

- css の疑似クラス `:indeterminate` に合致する状態。（[リンク](https://developer.mozilla.org/en-US/docs/Learn/Forms/UI_pseudo-classes#default_and_indeterminate)）
  - `<input/radio>`: 同じ名前のグループ内のすべてのラジオ ボタンが未チェック。
  - `<input/checkbox`: JavaScript で `indeterminate` プロパティが `true` になっている。
  - `<progress>`: 要素に値がない。
