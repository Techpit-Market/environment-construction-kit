> ここでは macOS における Laravel の環境構築方法を記載しています。対応バージョンは以下の通りです。
>
> - PHP 8.0.0
> - Laravel 6.0 (LTS)
>
> ここから教材

# Laravel の環境構築 (macOS)
Webアプリケーションを開発する環境を構築します。

今回は**Laravel 6.0**の環境構築を行います。

すでに Laravel 6.0 の環境が用意されていれば、この回は読み飛ばしてもかまいません。

::: warn
本パートは macOS での環境構築方法を記載しています
:::


## Homebrewをインストール
ソフトウェアの導入を簡単にするため、macOS用のパッケージ管理システムである**Homebrew**をインストールします。

次のリンク先からHomebrewをインストールします。

[Homebrew](https://brew.sh/index_ja.html)

リンク先にアクセスすると次のページが表示されます。

![image](https://i.gyazo.com/f50d715e69ae4e121735ca95454a3d0c.png)

「インストール」の見出しの下にあるスクリプトの行をmacOSのターミナルにコピー＆ペーストします。

ターミナルで実行するとHomebrewのインストールが開始されます。

インストールには数分~10分ほどかかります。途中で何度かパスワードを要求されるので、使用しているパソコンのパスワードを入力してください。


## Homebrewのインストールを確認
Homebrewのインストール後に、無事にインストールされたかどうかを確認します。

インストール後の確認は、ターミナルを起動して次のコマンドを入力します。

```console
brew -v
```

入力をしたら`enter`キーを押して、コマンドを実行します。

コマンドが実行されると、次のような画面になります。

```console
brew -v
Homebrew 2.7.0
Homebrew/homebrew-core (git revision 82e18e; last commit 2020-12-23)
Homebrew/homebrew-cask (git revision 8a9036; last commit 2020-12-23)
```

「Homebrew 2.7.0」とバージョンが表示され、Homebrewがインストールされたことが確認できました。

（執筆時は「2.7.0」と表示されましたが、「2.7.1」などと表示されると最新版がインストールされたことになります)


## PHPBrew をインストール

※作成中です
