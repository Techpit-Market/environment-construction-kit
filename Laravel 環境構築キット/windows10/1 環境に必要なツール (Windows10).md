> ここでは開発に使用するテキストエディタとして、VSCodeの紹介とインストール手順を記載しています。
>
> 「ターミナルの確認」の項ではWSL2を用いてインストールしたUbuntuのコンソールウインドウの開き方を説明しているので、Ubuntuを使用しない場合は開発環境に合わせて書きかえてください。
>
> 教材を作成するに当たって必要であれば説明を付け加えてください。
>
> ここから教材


# 開発に必要なツール (Windows10)
ここでは開発を進めるために必要なテキストエディタを紹介します。

はじめてテキストエディタやターミナルを使う人はぜひ参考にしてください。

これから紹介するテキストエディタは筆者の推奨例です。すでに使い慣れたテキストエディタがあれば、読み飛ばしてもかまいません。

::: warn
本パートは Windows10 での環境構築方法を記載しています。
:::

**※使用できるツールをほかに用意してある場合は、この回を読み飛ばしてもかまいません。**


## テキストエディタとは
テキストエディタとは、テキストファイルを作成・編集・保存するためのソフトウェアです。

本教材では、Microsoftが開発した無償利用ができるテキストエディタの**Visual Studio Code**を使って解説を行います。

（Visual Studio Codeは「VSCode」と通称され、本教材中でも「VSCode」と表記する場合があります）


## Visual Studio Code のインストール
Visual Studio Codeのインストール方法を説明します。

最初に、次のリンク先のページから「Visual Studio Code」をダウンロードしてください。

[【Visual Studio Codeのダウンロードページ】](https://code.visualstudio.com/)

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27735/7835127a-a7f3-4a05-a1d4-93cd8e8e29bf.png" alt="1">

ダウンロードが完了したら、ダウンロードしたファイルを開いてください。

ファイルを開くと、以下のようなウインドウが表示されるので、「同意する」を選択し、「次へ」ボタンをクリックしてください。

<img width="600" src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27727/519f36a4-b64e-41cf-8dfd-08ba222a6136.png" alt="2">

Visual Studio Codeをインストールするフォルダを指定する画面が表示されます。

特に理由がなければ、何も変更せずにそのまま「次へ」ボタンをクリックしてください。

<img width="600" src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27722/82361e60-8cf2-4152-87c4-c4aabdac2720.png" alt="3">

スタートメニューに表示するためのショートカットを作成するフォルダを指定する画面が表示されます。

<img width="600" src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27723/6b7117a1-ce64-4f73-994b-495e87d09200.png" alt="4">

スタートメニューとは画面左下にあるWindowsアイコンをクリックすると表示されるメニューのことを指します。

以下のようにVisual Studio Codeが格納されるフォルダを指定することができます。

<img width="600" src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27743/d4316704-3272-427d-89a1-ea9f03993c24.png" alt="4-2">

特にこだわりがなければ、何も変更せずに「次へ」ボタンをクリックしてください。

インストール時に実行する追加のタスクを指定する画面が表示されます。

<img width="600" src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27726/0fedc2be-b7d3-4499-a96e-b0acedb33887.png" alt="5">

特にこだわりが無ければ、何も変更せずに「次へ」ボタンをクリックしてください。

ここまで行なった設定を確認する画面が表示されます。

<img width="600" src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27724/3b563c25-e8f3-40a9-a81c-92247ecf6517.png" alt="6">

問題なければ「インストール」ボタンをクリックしてください。

以下のようにインストールが始まります。

<img width="600" src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27725/d23f1df4-4004-4c4c-8e1c-909bf4924f45.png" alt="7">

インストールが終わると、以下のような画面が表示されるので、「Visual Studio Codeを実行する」と表示されているチェックボックスをオンにし、「完了」ボタンをクリックしてください。

<img width="600" src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27729/25aa4806-4a79-4465-8d98-d5791a0f452f.png" alt="8">

以下のように、Visual Studio Codeのウインドウが表示されれば完了です。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27730/f3d25ed9-d376-43ac-9431-2682566033d7.png" alt="9">

## Visual Studio Code の設定をカスタマイズ
Visual Studio Codeはデフォルト設定でも利用できますが、ここでは扱いやすいように次のカスタマイズを行ないます（各自の好みで設定しても問題はありません）。

設定をはじめるには、画面左下の歯車アイコンをクリックして設定画面を開きます。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27738/e0cc5a66-e755-4e57-8151-d5250caa0287.png" alt="16">

設定画面が開いたら、以下の画像で示した、画面右上にあるアイコンをクリックします。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27736/ad4fa499-5744-4d3e-8c4b-dba93be4cafb.png" alt="17">

アイコンをクリックすると、次の画面のような`settings.json`ファイルが表示されます。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27731/48b25f28-879e-4972-815b-acbd9fc2e7b8.png" alt="18">

`settings.json`ファイルに以下のコードをコピーします（内容を理解する必要はありません）。 

```json:settings.json
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
（`Ctrl` + `S`キーを押して上書き保存ができます）

次の画像のように、画面左側に設定が表示されるとカスタマイズ完了です。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27740/d1a170e1-da55-4cbb-9cab-6e3381523680.png" alt="19">

## Visual Studio Codeの拡張機能をインストール
Visual Studio Codeで開発しやすくするため、さらに**拡張機能**を追加します。追加する拡張機能は次の3つです。

```
● PHP Intelephense
  → PHPのコード補完や定義への移動など様々な機能を提供。
● Japanese Language Pack for Visual Studio Code
  → VSCodeを日本語に対応したUIを提供。
● vscode-icons
  → ファイルやフォルダにアイコンを追加。
```

それでは拡張機能を追加します。

次の画像の左にある拡張機能アイコンをクリックしてください。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27739/897d15c9-c85d-4cb6-92c4-ffd3fed031ec.png" alt="20">

拡張機能の「MARKETPLACE」が表示されるので、検索バーでインストールする拡張機能を入力して検索します。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27741/423e775e-e44f-4607-a67d-b9e65e3e56da.png" alt="14">

まずは「PHP Intelephense」と検索します。

すると次の画像のように「PHP Intelephense」が表示されるのでインストールします。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27742/e95be46b-8183-4f69-a424-3ffbaaae888c.png" alt="15">

これで「PHP Intelephense」がインストールできました。

同じ方法で他の拡張機能もインストールしてください。

3つの拡張機能がインストールできたらVSCodeを**再起動**します。VSCodeが再起動されると拡張機能が使えるようになります。

## ターミナルを確認する
**ターミナル**は命令文（**コマンド**）を入力してWindows10の操作や設定を行なうためのツールです。

Ubuntuのコンソールウインドウもターミナルの一種です。

ここでは、Visual Studio Code上でUbuntuのコンソールウインドウを開く方法を説明します。

画面上部で「Terminal(ターミナル)」をクリックし、表示されたメニューから「New Terminal(新しいターミナル)」をクリックしてください。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27732/f212cd90-2207-42f1-9cdf-e718bc8e8cb5.png" alt="10">

以下のように、画面下部にターミナルが表示されます。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27733/16a0b511-c21b-483a-b51d-0c6c051ed015.png" alt="11">

ここで表示されているターミナルはWindows10に標準でインストールされているPowerShellというツールです。

Ubuntuのコンソールウインドウを開くには、画面右側にある「＋」アイコンの右にある下向きのアイコンをクリックし、表示されたメニューから「Ubuntu-20.24 (WSL)」をクリックします。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27737/15a60cb0-5da4-438c-88a6-42f9208ab2d0.png" alt="12">

以下のように、Ubuntuのコンソールウインドウが表示されます。

<img src="https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/27734/f84166cf-cb03-416a-8399-b13d4bc4f442.png" alt="13">

以上でこのパートは終了です。

お疲れ様でした。
