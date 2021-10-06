> ここでは Windows10 における Laravel の環境構築方法を記載しています。対応バージョンは以下の通りです。
>
> - PHP 8.0
> - Laravel 6系 (LTS)
>
> PHPの環境構築キットでasdfを用いてPHP8.0とComposerをインストールしていることを前提としています。
>
> プロジェクトディレクトリ名は「〇〇」と仮書きしているので、ご自身で書き換えてご使用ください。
>
> ここから教材

# Laravel 6の環境構築 (Windows10)
PHPのフレームワークである**Laravel**をインストールし、Webアプリケーションを開発する環境を構築します。

今回は**Laravel6系**の環境構築を行います。

Laravel6系は、LTS（Long Term Support）と呼ばれる、長期サポートが保証されている最新のバージョンです(2021年9月現在)。

## Laravel環境のプロジェクトディレクトリの作成
Laravel環境のプロジェクトディレクトリを作成し、Webアプリケーションを作成するためのベースとなる環境を構築します。

:::warn
このパートで実行するコマンドは、すべてUbuntuのコンソール ウィンドウで実行してください。
:::

プロジェクトディレクトリはお好きな場所に作成することができます。

あらかじめ、`cd`コマンドを用いて、プロジェクトディレクトリを置きたい場所に移動してください。

ホームディレクトリに作成する場合は以下のコマンドで移動できます。

```console
cd ~
```

Laravelをインストールするには、ComposerというPHPのパッケージ管理ツールを使用します。

以下のコマンドを実行してください。

```console
composer create-project laravel/laravel 〇〇 "6.*" --prefer-dist
```

コマンドの意味は以下の通りです。

|コマンド・オプション|説明|
|---|---|
|composer|ライブラリの管理ツールであるcomposerを使うためのコマンド|
|create-project {パッケージ} {ディレクトリ名(作成するアプリケーション名)} "{バージョン数}"|指定したパッケージを指定したディレクトリへインストールするためのコマンド|
|--prefer-dist|zip形式でダウンロードするためのオプション(高速にダウンロードできる)|

以下のようなメッセージが表示されれば、Laravel環境のプロジェクトディレクトリの作成は完了です。

```
Package manifest generated successfully.
68 packages you are using are looking for funding.
Use the `composer fund` command to find out more!
> @php artisan key:generate --ansi
Application key set successfully.
```

## ローカルサーバーの起動
プロジェクトディレクトリが作成できたら、Laravelアプリケーションを立ち上げ、ブラウザにLaraveの初期画面を表示させてみましょう。

まずは作成したプロジェクトディレクトリへ移動しましょう。

以下のコマンドを実行してください。

```console
cd 〇〇
```

プロジェクトディレクトリへ移動できたら、Laravelアプリケーションを立ち上げます。

以下のコマンドを実行してください。

```console
php artisan serve
```

以下のようなメッセージが表示されます。

```
Laravel development server started: http://127.0.0.1:8000
```

Laravelアプリケーションを起動したら、ブラウザで「http://localhost:8000/」にアクセスします。

次の画像のようにLaravelのデフォルトページが表示されていれば、うまく動作しています。

<img width="1142" alt="1-3-7" src="">

以上で今回のパートは終了です。

お疲れさまでした。
