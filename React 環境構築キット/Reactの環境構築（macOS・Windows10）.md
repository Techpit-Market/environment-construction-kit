> ここではmacOSとWindows10(WSL2・Ubuntu20.04)におけるReactの環境構築方法を記載しています。
>
> Node.jsがインストール済みであることを前提としているため、[「Node.js 環境構築キット」](https://github.com/Techpit-Market/environment-construction-kit/tree/master/Node.js%20%E7%92%B0%E5%A2%83%E6%A7%8B%E7%AF%89%E3%82%AD%E3%83%83%E3%83%88)も合わせて使用してください。
>
> プロジェクトディレクトリ名は「〇〇」と仮書きしているので、ご自身で書き換えてご使用ください。
>
> ここから教材

# Reactの環境構築（macOS・Windows10）
JavaScriptのフレームワークであるReactをインストールし、Webアプリケーションを開発する環境を構築します。

## 新規Reactプロジェクトの作成
React環境のプロジェクトディレクトリを作成し、Webアプリケーションを作成するためのベースとなる環境を構築します。

プロジェクトディレクトリは好きな場所に作成することができます。

あらかじめ、`cd`コマンドを用いて、プロジェクトディレクトリを置きたい場所に移動してください。

ホームディレクトリに作成する場合は以下のコマンドで移動できます。

```console
cd ~
```

Reactプロジェクトを作成するには、**npx**というコマンドを使用します。

`npx`はNode.jsのパッケージを管理する**npm**(Node Package Manager の略)で管理されているパッケージを簡単に実行することができるコマンドです。

`npx`コマンドを使用することで、Reactアプリの構築に必要な様々なパッケージをひとまとめにインストールしてくれます。

それではReactプロジェクトを作成しましょう。

以下のコマンドを実行してください。

```console
npx create-react-app 〇〇
```

上記コマンドを初めて実行する場合に限り、以下のメッセージが表示されます。

```
Need to install the following packages:
  create-react-app
Ok to proceed? (y)
```

`create-react-app`パッケージをインストールするか聞かれているので、「y」を入力してエンターキーを押してください。

以下のようなメッセージが表示されればReactプロジェクトの作成は成功です。

```
Success! Created react_sample at /Users/xxx/〇〇
Inside that directory, you can run several commands:

  ︙
  中略
  ︙

Happy hacking!
```

## ローカルサーバーの起動
プロジェクトディレクトリが作成できたら、Reactアプリケーションを立ち上げ、ブラウザにReactの初期画面を表示させてみましょう。

まずは作成したプロジェクトディレクトリへ移動しましょう。

以下のコマンドを実行してください。

```console
cd 〇〇
```

プロジェクトディレクトリへ移動できたら、Reactアプリケーションを立ち上げます。

```console
npm start
```

うまくサーバーが起動すると、ターミナルで以下のようなメッセージが表示されます。

```
Compiled successfully!

You can now view react_sample in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://192.168.1.4:3000

Note that the development build is not optimized.
To create a production build, use yarn build.
```

また、ブラウザが自動で開き、以下の画面のようにReactのデフォルトページが表示されていれば、うまく動作しています。

<img width="1040" src="https://user-images.githubusercontent.com/25563739/140449164-3ff7ef2e-08ac-4afe-b930-1914d0e7ced3.png">

もし自動でブラウザが開かない場合は、Google ChromeやSafariなどのブラウザを起動し、URL欄に`http://localhost:3000`を貼り付け、エンターキーを押すと画面が表示されます。

<img width="836" src="https://user-images.githubusercontent.com/25563739/140449673-fe5f387a-645e-4fb8-9a5d-5183551c5d4a.png">

以上で今回のパートは終了です。

お疲れさまでした。
