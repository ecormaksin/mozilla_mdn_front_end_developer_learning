# HTMLに関するメモ

## [ハイパーリンク](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)

- リンクの追加情報を含める場合は、`title` 属性を使う。ただし、マウスを当てている時しかツール チップとして表示されないので、重要な情報は通常のテキストにする。[link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#adding_supporting_information_with_the_title_attribute)

    <details><summary>例</summary><div>

    ```html
    <p>
      I'm creating a link to
      <a
        href="https://www.mozilla.org/en-US/"
        title="The best place to find more information about Mozilla's
              mission and how to contribute">the Mozilla homepage</a>.
    </p>
    ```

    </div></details></br>

- ファイルをダウンロードさせる場合は、 `download` 属性にデフォルトのファイル名を指定する。[link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#use_the_download_attribute_when_linking_to_a_download)

    <details><summary>例</summary><div>

    ```html
    <a
      href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=en-US"
      download="firefox-latest-64bit-installer.exe">
      Download Latest Firefox for Windows (64-bit) (English, US)
    </a>
    ```

    </div></details></br>

- 宛先を指定した状態でメール アプリを開く場合は、`<a>` タグで `href="mailto:<宛先のメール アドレス>"` を指定する。 [link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#email_links)

    <details><summary>例</summary><div>

    ```html
    <a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
    ```

    </div></details>

  - `<宛先のメール アドレス>` は任意。カンマ区切りで複数指定できる。
  - `mailto:` では、宛先だけでなく件名・CC・BCC・本文なども指定できる。[link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#specifying_details)
    - URLのクエリ パラメーターの指定と同じ方式
      - 各項目はURLエンコードする。
      - 不可視文字を含めない。（タブ・キャリッジ リターン・改行）
      - スペースは `%20` でエスケープする。
      - メール アドレスの後ろに `?` を付加する。
      - 各項目は `&` で区切る。

      <details><summary>例</summary><div>

      ```html
      <a
        href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&subject=The%20subject%20of%20the%20email&body=The%20body%20of%20the%20email">
        Send mail with cc, bcc, subject and body
      </a>
      ```

      </div></details></br>
