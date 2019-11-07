> ここでは開発に必要なツールの紹介、インストール手順を書きます。
>
> 教材を作成するに当たって必要であれば説明を付け加えてください。
>
> ここから教材


# 開発を進める上で必要なツール（macOS）
このパートでは開発を進める上で必要なツールを紹介します。ここで紹介しているツールはあくまで私のおすすめなツールなので、ご自身で慣れているツール等を既にお使いであればこのパートは読み飛ばしても構いません。初めてテキストエディタやターミナルを使う方は是非参考にしてください。

**※）今回のパートはPCがMacの方を対象としています。**

**※）既にお手元のMacにエディタがある方はこちらのパートを読み飛ばして構いません。**


## テキストエディタ
プログラミングをしていく上で必要であるテキストエディタを準備します。

テキストエディタとは、テキストファイルを作成・編集・保存するためのソフトウェアです。


## Visual Studio Code
本教材ではVisual Studio CodeというMicrosoftが開発したオープンソースのテキストエディタの導入方法を説明していきます。Visual Studio Codeは通称VSCodeと呼ばれ、無料で利用できます。


## Visual Studio Codeの導入方法
ではVisual Studio Codeのインストール方法を説明していきます。

まず以下のリンクからVisual Studio Codeをダウンロードしてください。

[Visual Studio Codeのダウンロードページ](https://code.visualstudio.com/)

![image](https://i.gyazo.com/ff452316e9ce484a7740129f9e0eeedf.png)

ダウンロードが完了したらダウンロードしたファイルを展開してください。そのあと展開したファイルをアプリケーションフォルダに移動してください。移動させる方法色々ありますが、下記の動画ではFinderを2つ開いてドラック&ドロップで移動させています。(Finderを2つ開くには、Finderを開いた状態で`command + N`を押すことで2つ開くことができます。)

![image](https://i.gyazo.com/917887a28214f07429f731b61f49a114.gif)

アプリケーションフォルダに移動できたら、Visual Studio Codeを起動してください。下記の画面のようになっていればうまく導入ができています。

![image](https://i.gyazo.com/3a9c885cbe0dbf2758f7162c859f569d.png)


## Visual Studio Codeをカスタマイズ
デフォルトでもプログラミングはできますが、より開発しやすくするためにカスタマイズをしていきます。

**※)カスタマイズに関してはお好みで設定されて大丈夫です。**

まず、`Command + ,`を押して設定画面を開きます。

![image](https://i.gyazo.com/3f73f9773290bcd25ded645ff3f35427.png)

検索ボックスに`settings.json`と打ち込んで`Enter`を押してください。`Edit in settings.json`というリンクが表示されますのでそれをクリックします。

![image](https://camo.githubusercontent.com/a3d28720d86b33ca9c998cc3d1cbb10e8b89a33b/68747470733a2f2f692e6779617a6f2e636f6d2f65636465633332376536333662396339396233373565336264626534393238342e706e67)

すると下のような画面になります。これは`settings.json`という設定ファイルに直接書き込みできるモードです。

![image](https://camo.githubusercontent.com/13f2f7cee29910890f0a0347fefd8e8189e7f359/68747470733a2f2f692e6779617a6f2e636f6d2f39323866333132633835613735343431303663393261656633366163643763342e706e67)

次に`settings.json`ファイルに以下のコードをコピーして、すでに書いてあるコードに上書きして保存してください。`command + S`で保存できます。（下記に示しているコードは、特に理解する必要はありません。）

```json
{
    // 差分を横に並べて表示ではなく行内に表示する
    "diffEditor.renderSideBySide": false,
    // ファイルを保存時に自動フォーマットする
    "editor.formatOnSave": true,
    // 現在の行を強調表示する
    "editor.renderLineHighlight": "all",
    // 空白文字を表示する。
    "editor.renderWhitespace": "all",
    // スペース2個インデント
    "editor.tabSize": 2,
    // ウィンドウ幅右端で折り返す
    "editor.wordWrap": "on",
    // ファイル保存時に最新の行を末尾に挿入する
    "files.insertFinalNewline": true,
    // アイコンテーマの指定
    "workbench.iconTheme": "vscode-icons"
}
```

上記のコードを追加したら下記の画像のように空白文字に「・・・・」と表示されていればカスタマイズがうまくできています。

![image](https://i.gyazo.com/02b74ac567ed7249b426a9d8e92bf685.png)

今回カスタマイズした内容はVSCodeを使っていくなかでお好みに変更されても構いません。


## 拡張機能の追加
より開発しやすくするために拡張機能を追加していきます。
追加する拡張機能は以下の3つです。

```
● PHP Intelephense
PHPのコード補完や定義への移動など様々な機能を提供。
● Japanese Language Pack for Visual Studio Code
VSCodeを日本語に対応したUIを提供。
● vscode-icons
ファイルやフォルダにアイコンを追加。
```

では拡張機能を追加していきます。下記の画像のように左側にあるアイコンをクリックしてください。

![image](https://i.gyazo.com/c177323e905539c651386e738b689e99.png)

すると拡張機能のMARKETPLACEが表示されるので、検索バーからインストールしたい拡張機能を検索しましょう。

![image](https://i.gyazo.com/182e29f848be2617b979606d4ae0dcd5.png)

まずは試しに「PHP Intelephense」と検索してみましょう。

すると下記の画像のように「PHP Intelephense」の拡張機能が表示されるのでインストールしてください。

![image](https://i.gyazo.com/f2aab5e0d20853c6b7e3b08fea56683a.png)

これでPHP Intelephenseの拡張機能がインストールできました。同じやり方で他の拡張機能もインストールしてみましょう。

全てインストールできたらVSCodeを**再起動**してください。再起動することで拡張機能が使えるようになります。


## ターミナル
ターミナルとは、コマンドと呼ばれる命令文を用いてMacの操作や設定を行うためのツールです。ターミナルに関しては、Macにはデフォルトで用意されているので、インストールする必要はありません。ターミナルはコマンドを入力する際に利用します。

見た目をかっこよくするためにターミナルをカスタマイズすることもできますが、[Hyper](https://hyper.is/)というツールもおすすめです。

またVSCodeにもターミナルはあります。下記の動画のようにVSCodeの下部をクリックするとターミナルを表示できます。なのでVSCode内にあるターミナルを利用してコマンドを実行することもできます。

![image](https://i.gyazo.com/7abaa72bf4a755af90822a45717798c9.gif)

以上で今回のパートは終了です。

お疲れ様でした。
