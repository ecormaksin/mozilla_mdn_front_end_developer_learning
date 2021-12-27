# The web and web standards webとwebの標準

## Brief history of the web / webの簡単な歴史

- 1960年代の後半
  - アメリカ陸軍が[ARPANET](https://developer.mozilla.org/en-US/docs/Glossary/Arpanet)と呼ばれるコミュニケーションのネットワークを開発した。
    - webの前身と言える。
      - [packet switching / パケットの切り替え](https://en.wikipedia.org/wiki/Packet_switching)を基盤として動作する。
      - [TCP/IP](https://en.wikipedia.org/wiki/Internet_protocol_suite)プロトコルで実装されている。

- 1980年
  - Tim Berners-Lee (よくTimBLと呼ばれる)がENQUIREと呼ばれるノートPC用のプログラムを書いた。
    - 異なるノード間のリンクという概念が盛り込まれていた。  
← インターネットと似てない？

- 1980年
  - TimBLが[Information Management: A Proposal /「情報管理: ある提案」](https://www.w3.org/History/1989/proposal.html)とHyperText / ハイパーテキスト をCERNで書いた。
    - この2つの発表が合わさって、webがどのように動くかの基盤を提示した。

- 1990年代の後半
  - TimBLがwebの第1版の実行に必要なすべての要素を作り出した。
    - [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP)
    - [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
    - [WorldWideWeb](https://en.wikipedia.org/wiki/WorldWideWeb)という名前の最初のwebブラウザー
    - HTTPサーバー
    - 閲覧対象のいくつかのwebページ

- それ以降の数年
  - webが爆発的に広まった。
    - 複数のwebブラウザーがリリースされた。
    - 数千台のwebサーバーがセットアップされた。
    - 数百万のwebページが作られた。

- 1994年
  - TimBLが[World Wide Web Consortium](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium)(W3C)を設立した。
    - webの技術仕様を作成するために、多くの異なる技術会社から、それぞれの代表者を招集する組織

## Web standards / web標準

- **web標準**
  - 私たちがwebサイトを構築する時に使う技術群のこと。
  - 仕様と呼ばれる技術文書がある限りは存続する。
    - 仕様: その技術がどのように動作するかを正確に説明するもの。
      - その技術をどのように使うかを学ぶには、あまり役に立たない。
- 例
  - [HTML Living Standard](https://html.spec.whatwg.org/multipage/)
    - HTML(HTMLの要素、それに関連するAPI群、その他の周辺技術すべて)がどのように実装されるべきかを、正確に説明している。
- web標準は標準化団体によって作られる。
  - W3C
  - [WHATWG](https://whatwg.org/)
    - HTML言語の現在有効な標準をメンテナンスする。
  - [ECMA](https://www.ecma-international.org/)
    - JavaScriptのベースとなるECMAScriptの標準を公開する。
  - [Khronos](https://www.khronos.org/)
    - WebGLのような3Dのグラフィックの技術を公開する。

### "Open" standards / "オープンな"標準

- web標準の鍵となる性質の1つ: 貢献するのも使うのも無料であること
  - TimBLとW3Cが当初から同意していた。
  - 特許やライセンスで妨げられてはならない。

### Don't break the web / webを壊すな

- "webを壊すな"
  - オープンなweb標準について聞くことのあるフレーズ。
  - 新しい技術はすべて後方互換性と前方互換性があるべきという考え方。
    - 後方互換性
      - その技術が導入される前に作られたwebサイトも、これまでと同様に動作するべき。
    - 前方互換性
      - 未来の技術は現在の技術と互換性があるべき。

## Being a web developer is good / web開発者になることは良いことだ

_変わらない唯一のことは、変化すること。_