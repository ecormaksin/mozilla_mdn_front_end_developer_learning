# Installing basic software / 基本的なソフトウェアをインストールする

## まとめ

色々なツールがあるけど、最低限テキスト エディタとWebブラウザがあればいいよ。
テキスト エディタのオススメはVisual Studio Codeだよ。

---

## What tools do the professionals use? / プロはどんなツールを使ってるの？

- **コンピューター** 当たり前と思う人もいるけど、このWebページをスマホや図書館にあるパソコンで読んでいる人がいるかもしれないよ。マジメにWeb開発しようと思ったら、Windows・macOS・Linuxが動くデスクトップかノート パソコンを買った方がいいよ。
- **テキスト エディター** これを使ってコードを書くよ。テキスト エディターとか、ハイブリッド エディターがあるよ。
  - テキスト エディター
    - [Visual Studio Code](https://code.visualstudio.com/)
    - [Notepad++](https://notepad-plus-plus.org/)
    - [Sublime Text](https://www.sublimetext.com/)
    - [Atom](https://atom.io/)
    - [GNU Emacs](https://www.gnu.org/software/emacs/)
    - [VIM](https://www.vim.org/)
  - ハイブリッド エディター
    - [Dreamweaver](https://www.adobe.com/products/dreamweaver.html)
    - [WebStorm](https://www.jetbrains.com/webstorm/)
- **グラフィック エディター** Webページに載せるイメージやグラフィックを作るよ。
  - 例
    - [GIMP](https://www.gimp.org/)
    - [Figma](https://www.figma.com/)
    - [Paint.NET](https://www.getpaint.net/)
    - [Photoshop](https://www.adobe.com/products/photoshop.html)
    - [Sketch](https://www.sketch.com/)
    - [XD](https://www.adobe.com/products/xd.html)
  - 補足
    - イメージとグラフィックの違い（[Quora](https://www.quora.com/What-are-the-differences-between-graphics-and-images#:~:text=An%20image%20is%20a%202,4%2Ddim%20(animation).) 参照）
      - イメージ
        - ラスター 画像
          - ラスター: 画像を色のついた格子状の点で表す場合のドット。（[weblio](https://ejje.weblio.jp/content/raster) 参照）
        - 「ピクセル」という点で構成される2次元の視覚的表現。
        - 点で構成されているので、拡大すると粗く見える。
      - グラフィック
        - ベクター 画像
          - 点とその間の線に基づく数学的な漸近値によって生成される視覚的な表現。
          - ベクター: ベクトル。方向と大きさを持つ量。（[weblio](https://ejje.weblio.jp/content/vector) 参照）
        - 画像を拡大しても粗くならない。
- **バージョン管理システム** 色々な目的・役割のために使うよ。[Git](https://git-scm.com/)が一番人気のあるバージョン管理システムだよ。Gitは[GitHub](https://github.com/)や[GitLab](https://gitlab.com/)のようなコード等を保存するサービスで使われているよ。
  - 目的・役割
    - ファイルをサーバー上で管理する。
    - プロジェクトでチームと協働する。
    - コードや資産を共有する。
    - 複数の人が同じファイルを編集した時の衝突を防ぐ。
- **FTPプログラム** 古いWebホスティング サービスで、ファイルをサーバー管理するために使われていたよ。（[Git](https://git-scm.com/)がFTPの役割を取って代わってきているよ。）下に挙げるソフトウェアも含めて、たくさんの(S)FTPプログラムがあるよ。
  - [Cyberduck](https://cyberduck.io/)
  - [Fetch](https://fetchsoftworks.com/)
  - [FileZilla](https://filezilla-project.org/)
- **自動化システム** コードのコンパクト化やテスト実行のような繰り返し行うタスクを、自動的に実行してくれるよ。
  - 代表的なソフトウェア
    - [Webpack](https://webpack.js.org/)
    - [Grunt](https://gruntjs.com/)
    - [Gulp](https://gulpjs.com/)
- ライブラリーやフレームワーク等、共通の機能を書くスピードを上げてくれるものがあるよ。
  - ライブラリー
    - あなたが書いたコードの中で役に立つように、すでに用意された機能を提供してくれるコードが、JavaScriptやCSSのファイルとして出来上がるよ。
  - フレームワーク
    - ライブラリーの考え方を一歩押し進めて、独自の構文を使ってコーディングする基盤を提供してくれるよ。
- 他にもたくさんのツールがあるよ！

---

## What tools do I actually need, right now? / 実際のところ、今すぐ必要なツールは何？

上のリストを見て ((((；ﾟДﾟ))))ｶﾞｸｶﾞｸﾌﾞﾙﾌﾞﾙ になるかもしれないけど、ほとんどのものは知らなくてもWeb開発できるよ。ε-(´∀｀*)ﾎｯ
この記事では、必要最低限のツール（テキスト エディター）と、いくつかのモダンなWebブラウザーをインストールしてもらうよ。

### Installing a text editor / テキスト エディターのインストール

あなたのコンピューターにはたぶん、基本的なテキスト エディターがもう入ってるよ。デフォルトなら、Windowsなら[メモ帳](https://en.wikipedia.org/wiki/Microsoft_Notepad)、macOSなら[テキスト エディット](https://en.wikipedia.org/wiki/TextEdit)、Linuxはディストリビューションによって色々だけど、Ubuntuなら[gedit](https://en.wikipedia.org/wiki/Gedit)が入ってるよ。

Web開発するなら、メモ帳やテキスト エディット以外のテキスト エディターを使った方がいいよ。私達は[Visual Studio Code](https://code.visualstudio.com/)をオススメするよ。無料だし、ライブ プレビューやコード ヒントの機能があるよ。

### Installing modern web browsers / モダンなWebブラウザーのインストール

さしあたって、コードを確認するために、いくつかのデスクトップWebブラウザーをインストールするよ。下の中からあなたのOSを選んで、好きなブラウザーのインストーラーをダウンロードするためのリンクをクリックしてね。

- Windows: [Firefox](https://www.mozilla.org/en-US/firefox/new/), [Chrome](https://www.google.com/chrome/browser/), [Opera](https://www.opera.com/), [Internet Explorer](https://windows.microsoft.com/en-us/internet-explorer/download-ie), [Microsoft Edge](https://www.microsoft.com/edge), [Brave](https://brave.com/) (Windows 7以上のバージョンなら、Edgeがデフォルトになっているよ。Internet Explorer(IE) 11もインストールできるけど、別のブラウザーをインストールした方がいいよ。補足: [IE11は2022年6月16日(日本時間)に、サポートが終了するよ。](https://www.ipa.go.jp/security/announce/ie_eos.html)))
- macOS: [Firefox](https://www.mozilla.org/en-US/firefox/new/), [Chrome](https://www.google.com/chrome/browser/), [Opera](https://www.opera.com/), [Safari](https://www.apple.com/safari/), [Brave](https://brave.com/) (macOSとiOSはSafariがデフォルトだよ。)
- Linux:  [Firefox](https://www.mozilla.org/en-US/firefox/new/), [Chrome](https://www.google.com/chrome/browser/), [Opera](https://www.opera.com/),  [Brave](https://brave.com/)

先に進む前に、最低2つのブラウザーをインストールして、テストできるように準備する方がいいよ。
