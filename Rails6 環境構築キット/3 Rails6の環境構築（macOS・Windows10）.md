> ここではmacOSとWindows10(WSL2・Ubuntu)におけるRuby on Railsの環境構築方法を記載しています。対応バージョンは以下の通りです。
>
> - Ruby 3.0.2
>   - https://www.ruby-lang.org/ja/downloads/
> - Rails 6.1.4.1
>   - https://rubygems.org/gems/rails/versions
>
> Rubyの環境構築キットでasdfを用いてRubyをインストールしていることを前提としています。
>
> Railsはローカルにインストールするため、`rails`コマンド実行時には`bundle exec`を付けています。
>
> ここから教材


# Ruby on Railsの環境構築（macOS・Windows10）
Rubyのフレームワークである**Ruby on Rails**をインストールし、Webアプリケーションを開発する環境を構築します。

今回はRuby on Rails 6系の環境構築を行ないます。

すでにRuby on Rails 6系の環境が用意されていれば、この回を読み飛ばしてもかまいません。

## Bundlerのインストール
最初に**Bundler**をインストールします。

Rubyでは**Gem**というライブラリを使いパッケージを管理しています。

Gemコマンドで簡単にインストールやアンインストールができますが、複数のGemを使うとGem同士で依存関係が生まれ、バージョン違いによる不具合が出てきます。

そこで、BundlerでGemのそれぞれのバージョンを正確に追跡し管理して、Rubyプロジェクトに一貫した環境を提供します。

参考：
- [Bundler](https://bundler.io/)
- [RubyGems](https://rubygems.org/)

Bundlerはデフォルトでインストールされている場合もあるので、以下のコマンドで確認しましょう。

```console
bundle -v
```

コマンドを実行し、以下のようなメッセージが表示されたらインストールされています。

```
Bundler version 2.2.22
```

もしバージョン数が表示されなければ、以下に進んでBundlerをインストールしましょう。

以下のコマンドを実行してください。

```console
gem install bundler
```

コマンドを実行するとインストールが始まります。

インストールされたBundlerのバージョンを確認しましょう。

次のコマンドを実行してください。

```console
bundler -v
```

コマンドの実行後、次のように表示されます。

```
Bundler version 2.2.22
```

「version 2.2.22」とバージョン情報が表示されました。

これでBundlerがインストール済みであることを確認できました。

## yarnをインストール

次に**yarn**をインストールします。

yarnはJavaScriptのライブラリの利用に必要なパッケージマネージャです。

yarnと互換性のあるnpmというパッケージマネージャもあります。しかし、Rails6ではWebpackerが標準になったことにより、yarnが必要です。

yarnもRubyと同様にasdfで管理することができます。

それでは、asdfを用いてyarnのインストールを行ないましょう。

### プラグインのインストール

まずはyarnを管理するためのプラグインをインストールします。

以下のコマンドを実行してください。

```console
asdf plugin-add yarn
```

コマンドを実行すると以下のようなメッセージが表示されます。

```
updating plugin repository...remote: Enumerating objects: 21, done.
remote: Counting objects: 100% (21/21), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 18 (delta 11), reused 9 (delta 5), pack-reused 0
Unpacking objects: 100% (18/18), 3.05 KiB | 66.00 KiB/s, done.
From https://github.com/asdf-vm/asdf-plugins
   232d2df..d51b43b  master     -> origin/master
HEAD is now at d51b43b feat: deck plugin (#509)
```

以下のコマンドを実行して、プラグインがインストールできたか確かめましょう。

```console
asdf plugin list
```

以下のように、yarn と表示されていれば成功です。

```
ruby
yarn
```

### yarnのインストール

次に最新のyarnをインストールします。

以下のコマンドを実行してください。

```console
asdf install yarn latest
```

コマンドを実行すると以下のようにメッセージが数十行表示されます。

```
・
・
・
gpg: keybox'~/.asdf/keyrings/yarn/pubring.kbx'が作成されました
gpg: ~/.asdf/keyrings/yarn/trustdb.gpg: 信用データベースができました
gpg: 鍵1646B01B86E50310: 公開鍵"Yarn Packaging <yarn@dan.cx>"をインポートしました
・
・
・
```

::: info
**エラーが発生した場合**
Macの方で、コマンドを実行すると以下のようなメッセージが表示されることがあります。

```
⛔ Missing one or more of the following dependencies: gpg
```

上記の場合、`gpg`というツールが必要とのことなので、Homebrewでインストールしましょう。

以下のコマンドを実行してください。

```console
brew install gpg
```

コマンドを実行すると以下のようなメッセージが表示されます。

```
・
・
・
==> Installing gnupg 
==> Pouring gnupg--2.3.3_1.big_sur.bottle.tar.gz
🍺  /usr/local/Cellar/gnupg/2.3.3_1: 149 files, 13.2MB
```

インストールできたか確認しましょう。

以下のコマンドを実行してください。

```console
gpg --version
```

以下のようにバージョン情報が表示されれば成功です。

```
gpg (GnuPG) 2.3.3
libgcrypt 1.9.4
Copyright (C) 2021 Free Software Foundation, Inc.
License GNU GPL-3.0-or-later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
・
・
・
```

もう一度yarnをインストールします。

以下のコマンドを実行してください。

```console
asdf install yarn latest
```

特にエラーが表示されなければ完了です。

:::


yarnがインストールできたか確かめましょう。

以下のコマンドを実行してください。

```console
asdf list yarn
```

以下のようなメッセージが表示されれば、インストール成功です。

```
 1.22.17
```

### バージョンを設定

インストールが完了したら、バージョンを使用する設定をしましょう。

以下のコマンドを実行してください。

```console
asdf global yarn latest
```

コマンドを実行しても特にメッセージは表示されません。

最後にyarnコマンドが使用できるか確認しましょう。

以下のコマンドを実行してください。

```console
yarn -v
```

以下のように、バージョン数が表示されれば成功です。

```
1.22.17
```

## Railsプロジェクトのディレクトリを作成
Rails Tutorialや入門書などでは、システム(グローバル)にRailsをインストールする手順が説明されていることが多いですが、ここではプロジェクト(ローカル)にインストールする手順を説明します。

ローカルにRailsをインストールすることで、プロジェクトごとに異なるバージョンのRailsを設定することができ、複数のバージョンを共存させることができます。

それではRailsをインストールするディレクトリを作成しましょう。

プロジェクトディレクトリは好きな場所に作成することができます。

あらかじめ、`cd`コマンドを用いて、プロジェクトディレクトリを置きたい場所に移動してください。

ホームディレクトリに作成する場合は以下のコマンドで移動できます。

```console
cd ~
```

今回は「**〇〇**」という名前のプロジェクトを作成します。

以下のコマンドを実行してください。

```console
mkdir 〇〇
```

`〇〇`ディレクトリが作成されました。

作成したディレクトリに移動しましょう。

以下のコマンドを実行してください。

```console
cd 〇〇
```

## Gemfileの作成
プロジェクト内のGemを管理するための`Gemfile`というファイルを作成します。

`Gemfile`は先ほどインストールしたBundlerを使って作成できます。

以下のコマンドを実行してください。

```console
bundle init
```

コマンドを実行すると、以下のようなメッセージが表示されます。

```
Writing new Gemfile to {プロジェクトディレクトリの場所}/〇〇/Gemfile
```

## Gemfileの編集
作成した`Gemfile`にインストールしたいGemを記述します。

以下のように、インストールしたいGemを記述します。

**【例】**

```Gemfile
gem 'gem名', 'バージョン指定'
```

ここではRailsをインストールするための記述を行ないます。

VSCodeなどのエディタで`Gemfile`を開き、以下のように編集してください。

```diff:Gemfile
# frozen_string_literal: true

source "https://rubygems.org"

git_source(:github) { |repo_name| "https://github.com/#{repo_name}" }

-# gem "rails"
+gem 'rails', '6.1.4.1'
```

ファイルを編集できたら保存してください。

VSCodeの場合は`command(⌘) + s`キーで保存できます。

## Railsのインストール
Gemfileに記述したGemをインストールするには、以下のコマンドを実行します。

```console
bundle install --path vendor/bundle
```

以下のようなメッセージが表示されます。

```
・
・
・
Bundle complete! 1 Gemfile dependency, 41 gems now installed.
Bundled gems are installed into `./vendor/bundle`
```

`bundle install`コマンドを実行すると、Gemfileの内容に従いGemのインストールが行われます。

`--path vendor/bundle`と付けることで、`vendor/bundle`というディレクトリにGemがインストールされます。

## Railsのバージョンを確認

Railsをインストールしたら、Railsのバージョンを確認するために次のコマンドを入力します。

```console
bundle exec rails -v
```

コマンドを実行すると以下のようなメッセージが表示されます。

```
Rails 6.1.4.1
```

「`Rails 6.1.4.1`」と表示されました。

これで無事にRuby on Railsのインストールが完了しました。

::: info
**`bundle exec`について**

Railsのバージョン確認で`bundle exec rails -v`コマンドを実行しました。
単に`rails -v`としても良さそうですが、ローカルにインストールしたRailsを使用する場合は`bundle exec`を頭に付ける必要があります。
`bundle exec`を頭に付けずに実行すると、システム(グローバル)にインストールしたRailsを使用してしまうので注意しましょう。
:::

以上でこのパートは終了です。

お疲れ様でした。
