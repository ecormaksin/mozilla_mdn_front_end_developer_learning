# CSS に関するメモ

- Webブラウザーは「 [ユーザー エージェント(user agent)](https://developer.mozilla.org/en-US/docs/Glossary/User_agent) 」と呼ばれることがある。（ [リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/What_is_CSS#what_is_css_for) ）
  - コンピューター システム内で、1人の人間の代理になるプログラムを意味する。別の文脈でコンピューター システムを扱う場合では、Webブラウザー以外のプログラムがユーザー エージェントになりうる。</br></br>

- CSS セレクター
  - [セレクター全集](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_selectors)

  - 要素の絞り込み、**descendant(子孫) combinator**（[リンク1](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/Getting_started#styling_things_based_on_their_location_in_a_document), [リンク2](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#descendant_combinator)）

    - `li em { /* */ }`
      `<li>` タグの **中** の `<em>` タグの要素が対象。</br></br>

  - 直下の要素の指定、**child combinator**（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#child_combinator)）

    - `article > p { /* */ }`
      `<article>` タグの **直下** の `<p>` タグの要素が対象。</br></br>

  - ある要素の次の要素を指定、**next-sibling(兄弟) conbinator**（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#next-sibling_combinator)）

    - `h1 + p { /* */ }`
      `<h1>` タグの **次** の `<p>` タグの要素が対象。</br></br>

  - 任意の後続要素を指定、**subsequent-subling combinator**（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#subsequent-sibling_combinator)）

    - `p ~ img { /* */ }`
      `<p>` タグ **以降** の `<img>` タグが対象。</br></br>

  - 属性セレクター（attribute selectors）（[リンク1](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors#attribute_selectors)、[リンク2](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors#presence_and_value_selectors)）

    | セレクター | 例 | 説明 |
    | --- | --- | --- |
    | `[attr]` | `a[title]` | `attr` に指定した属性を持つ |
    | `[attr=value]` | `a[href="https://example.com"]` | ・`attr` に指定した属性を持つ  </br>・`value` が完全に一致する |
    | `[attr~=value]` | `p[class~="special"]` | ・`attr` に指定した属性を持つ </br>・`value` が完全に一致している </br>&nbsp;&nbsp;&nbsp;&nbsp;または </br>&nbsp;&nbsp;&nbsp;&nbsp;スペースで区切られた値のどれかに当てはまる |
    | `[attr\|=value]` | `div[lang\|="zh"]` | ・`attr` に指定した属性を持つ </br>・`value` が完全に一致している </br>&nbsp;&nbsp;&nbsp;&nbsp;または </br>&nbsp;&nbsp;&nbsp;&nbsp;指定した値の後にハイフンが続いている |

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
          - html: `<div class="notebox warning"><!-- --></div>` </br></br>

    - IDセレクター（id selector）
      - `#` 始まりの大文字・小文字の区別ありの名前をつける。
      - 名前はhtmlドキュメント内要素の `id` プロパティに一致するものが適用対象。（cssファイルでは `#` 始まりだけれども、htmlファイルでは `#` がつかない。）</br></br>

    - 要素指定の指針
      - IDセレクターよりも、クラス セレクターで指定した方がよい。（IDは1ページに1つしか定義できない値のため。）
      - IDでしか要素を指定できない状況の場合（htmlファイルの編集権限がない等）、 `p[id="header"]` のような属性セレクターを検討する。</br></br>

  - 部分文字列のセレクター（substring matching selectors）（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors#substring_matching_selectors)）

    | セレクター | 例 | 説明 |
    | --- | --- | --- |
    | `[attr^=value]` | `li[class^="box-"]` | ・`attr` に指定した属性を持つ </br>・`value` で始まる値|
    | `[attr$=value]` | `li[class$="-box"]` | ・`attr` に指定した属性を持つ </br>・`value` で終わる値|
    | `[attr*=value]` | `li[class*="box"]` | ・`attr` に指定した属性を持つ </br>・`value` をどこかに含む値 |

  - 入れ子による複雑なセレクターの作成
    - [リンク1](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_nesting/Using_CSS_nesting#combinators)
    - [リンク2](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_selectors/Selector_structure#complex_selector)

  - 大文字・小文字の区別（case-sensitivity）（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors#case-sensitivity)）
    - 大文字・小文字の区別なしで要素を指定したい場合、`li[class^="a" i] { /* */ }` のように、角括弧を閉じる前に `i` を指定する。</br></br>

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
    - 短縮形の記述方法で値を省略すると、初期値に戻ってしまう。</br></br>

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

- CSSルールの優先順位（[リンク](https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade#complete_cascade_order)）
  - アルゴリズム（判定順序）
    - ①関連度（Relevance）: 要素に該当するセレクターや `@media` で規定されたユーザー エージェント
    - ②定義されている場所と重要度（Origin and importance）
    - ③詳細度（specificity）
    - ④適用範囲の近接度（Scoping proximity）: [詳細リンク](https://developer.mozilla.org/en-US/docs/Web/CSS/@scope#how_scope_conflicts_are_resolved)
    - ⑤定義順（Order of appearance）</br></br>

  - 属性と値の組み合わせによる定義(property/value pair declarations)だけが、段階的適用に関与する。識別子(descriptors)を含んだ `@font-face` ルールのような、定義以外の要素を持つ `at-rules` は、段階的適用には関与しない。そのような `at-rules` に関しては、定義のように部分的・段階的に適用されるのではなく、最適なルール1つ全体が適用される。複数の適合候補が存在する場合は、上記の①②④の判定順序が使われる。（`at-rules` には③の詳細度が存在しないため。）</br></br>

  - CSSのアニメーションと段階的適用（[リンク](https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade#css_animations_and_the_cascade)）
    - CSSアニメーションは、`@keyframes` ルールを使って状態間の動きを定義する。同じ名前で 複数の `@keyframes` ルールが定義されている場合、定義場所とレイヤーの優先順位に基づいて最後のものが適用される。属性と値の組み合わせによる定義のように段階的には適用されない。

- CSSスタイルの継承（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance#inheritance)）
  - 子要素に継承されるスタイルもあれば、そうでないものもある。
  - [MDNのCSSプロパティ リファレンス ページ](https://developer.mozilla.org/en-US/docs/Web/CSS)の「 `Formal definition` 」に、継承されるかどうかが記載されている。（例: [color](https://developer.mozilla.org/en-US/docs/Web/CSS/color#formal_definition) プロパティ）</br></br>

- 継承の制御（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance#controlling_inheritance)）
  - `inherit`
    - 親要素からのスタイルを明示的に継承する。
  - `initial`
    - [MDNのCSSプロパティ リファレンス ページ](https://developer.mozilla.org/en-US/docs/Web/CSS)の「 `initial value` 」に定義されている内容。継承されているかどうかで適用されるルールが異なる。（[リンク](https://developer.mozilla.org/en-US/docs/Web/CSS/initial_value)）
    - ※ブラウザーのデフォルト スタイルではない。
  - `revert`
    - ブラウザーのデフォルト スタイルを適用する。
    - 多くの場合、`unset` と同じように作用する。
  - `revert-layer`
    - 一つ前の 「 [カスケード レイヤー（cascade layer）](https://developer.mozilla.org/en-US/docs/Web/CSS/@layer) 」で定義された値が適用される。
  - `unset`
    - `inherit` で継承された値が適用される。そうでない場合は `initial` のように作用する。

- セレクターの詳細度（[リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance#specificity_2)）
  - ID, クラス, 要素（タグ）を3桁の数値で表すことで測定できる。

    | ID | クラス | 要素 |
    | --- | --- | --- |
    | 百の位 | 十の位 | 一の位 |

    - 補足
      - クラス: 属性セレクターと疑似クラスも含める。
      - 要素: 疑似要素も含める。
      - universal セレクター（`*`）、combinators（`+`, `>`, `~`, `''`）と詳細度調整セレクター(specificity adjustment selector)は、詳細度に影響を与えない。

  - 否定(`negation`)（`:not()`）、関連(`relational`)（`:has()`）、`matches-any`（`:is()`）とCSSの入れ子(CSS nesting)自体は詳細度には影響せず、それらに対する引数や内包されたルールが影響する。引数に指定されたセレクターの中で詳細度が最も高いもの、内包されたルールの中で詳細度が最も高いものが適用される。

  - 例

    || ID | クラス | 要素 | 個人の理解メモ |
    | --- | --- | --- | --- |--- |
    | `h1` | 0 | 0 | 1 | 要素セレクター1個だけ |
    | `h1 + p::first-letter` | 0 | 0 | 3 | 要素セレクター2個 ＋ 疑似要素1個 |
    | `li > a[href*="en-US"] > .inline-warning` | 0 | 2 | 2 | クラス セレクター2個 ＋ 要素セレクター2個 |
    | `#identifier` | 1 | 0 | 0 | IDセレクター1個 |
    | `button:not(#mainBtn, .cta)` | 1 | 0 | 1 | `:not()` 自体は測定に含めない。パラメーター内で最も詳細度の高いものが採用されるので、IDセレクター1個 ＋ 要素セレクター1個 |

- CSSのレイヤー（cascade layer）
  - リンク
    - [リンク1](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_layers#the_layer_block_at-rule_for_named_and_anonymous_layers)
  - `@layer` で名前付きの規則のブロックを定義する時、既に同じ名前が存在する場合は規則が追加される。
