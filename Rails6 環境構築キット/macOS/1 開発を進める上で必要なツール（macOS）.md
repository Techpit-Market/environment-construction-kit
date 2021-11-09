> ここでは開発に必要なツールの紹介、インストール手順を書きます。
>
> 教材を作成するに当たって必要であれば説明を付け加えてください。
>
> ここから教材


# 開発に必要なツール

ここでは開発を進めるために必要なツールを紹介します。

はじめてテキストエディタやターミナルを使う人はぜひ参考にしてください。

これから紹介するツールは筆者の推奨例です。すでに使い慣れたツールがあれば、読み飛ばしてもかまいません。

**※本教材ではMac環境を例にして解説しています。**

**※使用できるツールをほかに用意してある場合は、この回を読み飛ばしてもかまいません。**


## テキストエディタ
プログラミングに必要な**テキストエディタ**を準備します。

テキストエディタとは、テキストファイルを作成・編集・保存するためのソフトウェアです。

本教材では、Microsoftが開発した無償利用ができるテキストエディタの**Visual Studio Code**を使って解説を行います。

（Visual Studio Codeは「VSCode」と通称され、本教材中でも「VSCode」と表記する場合があります）


## Visual Studio Codeのインストール
Visual Studio Codeのインストール方法を説明します。

最初に、次のリンク先のページから「Visual Studio Code」をダウンロードしてください。

[【Visual Studio Codeのダウンロードページ】](https://code.visualstudio.com/)

![image](https://i.gyazo.com/ff452316e9ce484a7740129f9e0eeedf.png)

ダウンロードが完了したら、ダウンロードしたファイルを展開し、Visual Studio Codeのファイルを「アプリケーション」フォルダに移動します。

ファイルの移動方法はさまざまですが、次の動画ではFinderを2つ開いてドラッグ&ドロップで移動しています。

(Finderを開いた状態で`command` + `N`キーを押せば、さらにFinderを開くことができます)

![image](https://i.gyazo.com/917887a28214f07429f731b61f49a114.gif)

「アプリケーション」フォルダに移動したら、Visual Studio Codeアイコンをクリックしてください。
Visual Studio Codeが起動して、次の画面が表示されたらインストールの完了です。

![image](https://i.gyazo.com/3a9c885cbe0dbf2758f7162c859f569d.png)


## Visual Studio Codeの設定をカスタマイズする
Visual Studio Codeはデフォルト設定でも利用できますが、ここでは扱いやすいように次のカスタマイズを行います（各自の好みで設定しても問題はありません）。

設定をはじめるには、`Command` + `,`キーを押すか、画面左下の歯車アイコンをクリックして設定画面を開きます。

![image](https://i.gyazo.com/3f73f9773290bcd25ded645ff3f35427.png)

設定ファイルに直接書き込みができる**settings.jsonモード**にします。

検索ボックスに「`settings.json`」と入力して`Enter`キーを押すと、「Edit in settings.json」というリンクが表示されます。

![image](https://camo.githubusercontent.com/a3d28720d86b33ca9c998cc3d1cbb10e8b89a33b/68747470733a2f2f692e6779617a6f2e636f6d2f65636465633332376536333662396339396233373565336264626534393238342e706e67)

「Edit in settings.json」リンクをクリックすると、次の画面のような`settings.json`ファイルが表示されます。

![image](https://camo.githubusercontent.com/13f2f7cee29910890f0a0347fefd8e8189e7f359/68747470733a2f2f692e6779617a6f2e636f6d2f39323866333132633835613735343431303663393261656633366163643763342e706e67)

`settings.json`ファイルに以下のコードをコピーします（内容を理解する必要はありません）。


```json
{
    // 差分を横に並べて表示せずに、行内に表示する
    "diffEditor.renderSideBySide": false,
    // ファイル保存時に自動フォーマットする
    "editor.formatOnSave": true,
    // 現在の行を強調表示する
    "editor.renderLineHighlight": "all",
    // 空白文字を表示する
    "editor.renderWhitespace": "all",
    // スペース2個分のインデント
    "editor.tabSize": 2,
    // ウィンドウ幅右端で折り返す
    "editor.wordWrap": "on",
    // ファイル保存時に新しい行を末尾に挿入する
    "files.insertFinalNewline": true,
    // アイコンテーマの指定
    "workbench.iconTheme": "vscode-icons"
}
```

このコードをコピー＆ペーストしたら、`settings.json`ファイルを上書きして保存します。
（`command` + `S`キーを押して上書き保存ができます）

次の画面のように、空白文字に「・・・・」が表示されるとカスタマイズは完了です。

![image](https://i.gyazo.com/02b74ac567ed7249b426a9d8e92bf685.png)


## Visual Studio Codeの拡張機能をインストールする
Visual Studio Codeで開発しやすくするため、さらに**拡張機能**を追加します。
追加する拡張機能は次の3つです。

```
● Ruby
  → VSCodeに対するRuby言語とデバッグサポートを提供する。

● Japanese Language Pack for Visual Studio Code
  → 日本語対応のVSCodeのUIを提供する。

● vscode-icons
  → ファイルやフォルダにアイコンを追加する。
```

それでは拡張機能を追加します。

次の画像の左にある拡張機能アイコンをクリックしてください。

![image](https://i.gyazo.com/c177323e905539c651386e738b689e99.png)

拡張機能の「MARKETPLACE」が表示されるので、検索バーでインストールする拡張機能を入力して検索します。

![image](https://i.gyazo.com/182e29f848be2617b979606d4ae0dcd5.png)

まずは「Ruby」を検索します。

すると次の画像のようにRubyが表示されるのでインストールします。

![image](https://i.gyazo.com/53bc02340dd67abd8c2b1a2cf8c63aa0.png)

これでRubyがインストールできました。

同じ方法で、「Japanese Language Pack for Visual Studio Code」「vscode-icons」を検索して、それぞれインストールをしてください。

3つの拡張機能のインストールができたら、VSCodeを**再起動**します。VSCodeが再起動されると拡張機能が使えるようになります。


## ターミナルを確認する
**ターミナル**は命令文（**コマンド**）を入力してMacの操作や設定を行うためのツールです。

ターミナルはMacのデフォルトで用意されているため、新たにインストールする必要はありません。

ターミナルを起動するには、MacのFinderで「アプリケーション」―「ユーティリティ」フォルダを開いて、「ターミナル」をダブルクリックします。

また、Visual Studio Codeにもターミナルはあります。次の動画のようにVisual Studio Codeの画面下部をクリックすればターミナルが表示され、コマンドの実行ができます。

![image](https://i.gyazo.com/7abaa72bf4a755af90822a45717798c9.gif)

以上でこの回は終了です。

お疲れ様でした。
