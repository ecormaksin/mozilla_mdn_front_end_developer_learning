# CSS に関するメモ

- Webブラウザーは「 [ユーザー エージェント(user agent)](https://developer.mozilla.org/en-US/docs/Glossary/User_agent) 」と呼ばれることがある。（ [リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/What_is_CSS#what_is_css_for) ）
  - コンピューター システム内で、1人の人間の代理になるプログラムを意味する。別の文脈でコンピューター システムを扱う場合では、Webブラウザー以外のプログラムがユーザー エージェントになりうる。<br /><br />

- CSS セレクター
  - 要素の絞り込み、**descendant(子孫) combinator**（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/Getting_started#styling_things_based_on_their_location_in_a_document)）

    ```css
    li em {
      color: rebeccapurple;
    }
    ```

    `<li>` タグの **中** の `<em>` タグの要素が対象。

  - ある要素の次の要素を指定、**next-sibling(兄弟) conbinator**

    ```css
    h1 + p {
      font-size: 200%;
    }
    ```

    `<h1>` タグの **次** の `<p>` タグの要素が対象。<br /><br />

- 同じHTML要素に複数のスタイルが指定されていた場合、後ろに記述しているスタイルが適用される。
  CSSクラスとHTML要素が同じ対象を指し示している時、CSSクラスが適用される。
  （ [リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured#specificity) ）

- property + value = declaration
  declarations を包含 → declaration blocks
  declaration blocks + selector = CSS rulesets or CSS rules
  （[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured#properties_and_values)）

- 関数による値の指定（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured#functions)）
  - 例
    - `calc()`: `width` に対する指定など
    - `rotate()`: `transform` に対する指定など

- `@rules`（発音: "at-rules"）
  - 例
    - `@import`: 他のCSSファイルをインポートする
    - `@media`: ユーザー エージェントによる条件付き適用

- 短縮形の値指定（shorthand properties）
  - 1つのプロパティで複数の値を指定する。
    - 4個の値（`padding`など）: 上、右、下、左（時計回り）
    - 2個の値: 上下、左右
  - 注意
    - 短縮形の記述方法で値を省略すると、初期値に戻ってしまう。

- 無効なプロパティや値は無視される。
  以下の場合に有用。
  - スペルミス
  - 新しいCSSのため、ブラウザーがまだサポートしていない。
    あるいは
    ブラウザーの方が古くて、対象のCSSに対応していない。
    - 古いブラウザーを考慮する場合は、対象のスタイルを2行分記述する方法がある。
      1行目: 古い書き方
      2行目: 新しい書き方

        ```css
        .box {
          width: 500px;
          width: calc(100% - 50px);
        }
        ```

- セレクター
  - 属性セレクター（attribute selectors）（[リンク1](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors#attribute_selectors)、[リンク2](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors#presence_and_value_selectors)）

    | セレクター | 例 | 説明 |
    | --- | --- | --- |
    | `[attr]` | `a[title]` | `attr` に指定した属性を持つ |
    | `[attr=value]` | `a[href="https://example.com"]` | ・`attr` に指定した属性を持つ  </br>・`value` が完全に一致する |
    | `[attr~=value]` | `p[class~="special"]` | ・`attr` に指定した属性を持つ </br>・`value` が完全に一致している </br>&nbsp;&nbsp;&nbsp;&nbsp;または </br>&nbsp;&nbsp;&nbsp;&nbsp;スペースで区切られた値のどれかに当てはまる |
    | `[attr\|=value]` | `div[lang\|="zh"]` | ・`attr` に指定した属性を持つ </br>・`value` が完全に一致している </br>&nbsp;&nbsp;&nbsp;&nbsp;または </br>&nbsp;&nbsp;&nbsp;&nbsp;指定した値の後にハイフンが続いている |

  - [セレクター全集](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_selectors)

  - 型セレクター、クラス セレクター、IDセレクター（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors)）
    - 型セレクター（type selector）、タグ名セレクター、要素セレクター
    - ユニバーサル セレクター（universal selector）
      - `*` で表記する。
      - 複数のコンビネーターと組み合わせて、適用対象を絞り込める。
        - 以下の記述は同じ機能だけれども、後者の方が意図が明確になる。

          ```css
          article :first-child { /* */ }

          article *:first-child { /* */ }
          ```

    - クラス セレクター（class selector）
      - `.` 始まりの大文字・小文字の区別ありの名前をつける。
      - `span.highlight` のように、特定のタグとクラス名を持つ要素に絞り込める。
      - 複数のクラスを持つ要素にも絞り込める。
        - 例
          - css: `.notebox.warning { /* */ }`
          - html: `<div class="notebox warning"><!-- --></div>`

    - IDセレクター（id selector）
      - `#` 始まりの大文字・小文字の区別ありの名前をつける。
      - 名前はhtmlドキュメント内要素の `id` プロパティに一致するものが適用対象。（cssファイルでは `#` 始まりだけれども、htmlファイルでは `#` がつかない。）

    - 要素指定の指針
      - IDセレクターよりも、クラス セレクターで指定した方がよい。（IDは1ページに1つしか定義できない値のため。）
      - IDでしか要素を指定できない状況の場合（htmlファイルの編集権限がない等）、 `p[id="header"]` のような属性セレクターを検討する。

  - 部分文字列のセレクター（substring matching selectors）（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors#substring_matching_selectors)）

    | セレクター | 例 | 説明 |
    | --- | --- | --- |
    | `[attr^=value]` | `li[class^="box-"]` | ・`attr` に指定した属性を持つ </br>・`value` で始まる値|
    | `[attr$=value]` | `li[class$="-box"]` | ・`attr` に指定した属性を持つ </br>・`value` で終わる値|
    | `[attr*=value]` | `li[class*="box"]` | ・`attr` に指定した属性を持つ </br>・`value` をどこかに含む値 |

  - 大文字・小文字の区別（case-sensitivity）（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors#case-sensitivity)）
    - 大文字・小文字の区別なしで要素を指定したい場合、`li[class^="a" i] { /* */ }` のように、角括弧を閉じる前に `i` を指定する。
