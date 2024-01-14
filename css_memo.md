# CSS に関するメモ

- Webブラウザーは「 [ユーザー エージェント(user agent)](https://developer.mozilla.org/en-US/docs/Glossary/User_agent) 」と呼ばれることがある。（ [リンク](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/What_is_CSS#what_is_css_for) ）
  - コンピューター システム内で、1人の人間の代理になるプログラムを意味する。別の文脈でコンピューター システムを扱う場合では、Webブラウザー以外のプログラムがユーザー エージェントになりうる。

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

    `<h1>` タグの **次** の `<p>` タグの要素が対象。
