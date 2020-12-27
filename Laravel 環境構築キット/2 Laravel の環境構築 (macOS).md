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
次に、PHP のバージョンを簡単に切り替えられる**PHPBrew**をインストールします。

公式ドキュメント: [PHPBrew](https://github.com/phpbrew/phpbrew)

それでは、以下のコマンドを順番に実行してください。

::: info
PHPBrew のインストール方法は公式ドキュメントの [Quick Start](https://github.com/phpbrew/phpbrew/wiki/Quick-Start) を参考にしています。

参考: [phpbrew - Quick Start](https://github.com/phpbrew/phpbrew/wiki/Quick-Start)
:::

```console
curl -L -O https://github.com/phpbrew/phpbrew/raw/master/phpbrew
chmod +x phpbrew

sudo mv phpbrew /usr/local/bin/phpbrew
phpbrew init
```

`sudo mv phpbrew /usr/local/bin/phpbrew` を実行したときに`password`を入力する必要があります。ご自身のPCのパスワードを入力してください。

`phpbrew init` を実行した際に以下のように表示されればOKです！

```console
phpbrew init
Using root: /Users/user_name/.phpbrew
Initialization successfully finished!
<=====================================================>
Phpbrew environment is initialized, required directories are created under

    /Users/user_name/.phpbrew

Paste the following line(s) to the end of your ~/.bashrc and start a
new shell, phpbrew should be up and fully functional from there:

    source /Users/user_name/.phpbrew/bashrc

To enable PHP version info in your shell prompt, please set PHPBREW_SET_PROMPT=1
in your `~/.bashrc` before you source `~/.phpbrew/bashrc`

    export PHPBREW_SET_PROMPT=1

To enable .phpbrewrc file searching, please export the following variable:

    export PHPBREW_RC_ENABLE=1


For further instructions, simply run `phpbrew` to see the help message.

Enjoy phpbrew at $HOME!!

<=====================================================>
```

また bash をお使いの場合は、以下のコマンドを実行してください。

```console
echo "[[ -e ~/.phpbrew/bashrc ]] && source ~/.phpbrew/bashrc" >> ~/.bashrc
```

次に、`source`というコマンドで追加した内容を反映します。

```console
source ~/.phpbrew/bashrc
```

最後に PHPBrew をアップデートします。

```console
phpbrew update
```


## PHP をインストール
次に**PHP**をインストールします。

PHP をインストールする前に、インストールできるPHPのバージョンを確認します。

先ほどインストールした PHPBrew を使って次のコマンドを実行してください。

```console
phpbrew known
```

コマンドを実行すると、インストールできるPHPのバージョンが表示されます。

```console
phpbrew known
Read local release list (last update: 2020-12-27 11:20:37 UTC).
You can run `phpbrew update` or `phpbrew known --update` to get a newer release list.
8.0: 8.0.0 ...
7.4: 7.4.13, 7.4.12, 7.4.11, 7.4.10, 7.4.9, 7.4.8, 7.4.7, 7.4.6 ...
7.3: 7.3.25, 7.3.24, 7.3.23, 7.3.22, 7.3.21, 7.3.20, 7.3.19, 7.3.18 ...
7.2: 7.2.34, 7.2.33, 7.2.32, 7.2.31, 7.2.30, 7.2.29, 7.2.28, 7.2.27 ...
7.1: 7.1.33, 7.1.32, 7.1.31, 7.1.30, 7.1.29, 7.1.28, 7.1.27, 7.1.26 ...
7.0: 7.0.33, 7.0.32, 7.0.31, 7.0.30, 7.0.29, 7.0.28, 7.0.27 ...
```

本教材では、「8.0.0」をインストールします。

それでは、次のコマンドを実行して PHP 8.0.0 をインストールします。

```console
phpbrew install 8.0.0
```

※作成中です
