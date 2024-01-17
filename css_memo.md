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
