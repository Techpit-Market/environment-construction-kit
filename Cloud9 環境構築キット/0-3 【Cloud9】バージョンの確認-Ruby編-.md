# 【Cloud9】バージョンの確認

この章では、RubyおよびRuby on Railsのバージョンを確認していきます。

なお、この教材ではRubyのバージョンは○○、Ruby on Railsのバージョンは○○を推奨しています。

>↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑
>○○に教材のバージョンを入れる


## Rubyのバージョンを確認する

以下のURLからコンソールにサインインして、Cloud9を立ち上げましょう。

https://us-east-2.console.aws.amazon.com/console/

Cloud9上のTerminalを立ち上げて、以下のコマンドを実行してRubyのバージョンを確認しましょう。

```bash
$ ruby -v
```

以下のように数字が表示されます。
ここではRubyの環境が「**2.6.3**」であることがわかります。

Cloud9のRubyのバージョンが本教材のバージョンと同じであれば、「**Railsのバージョンを確認する**」まで読み飛ばしてください。

```bash
$ ruby -v
ruby 2.6.3p62 (2019-04-16 revision 67580) [x86_64-linux]
```

## Rubyのバージョン確認とインストール

それではここからRubyのインストールを行っていきます。

Cloud9にはデフォルトでRubyがインストールされていますが、バージョンが古い可能性があるため、併せて確認していきましょう。

以下のコマンドを実行して、表示されるバージョンがこの教材と同じバージョンであればこのステップは不要です。**Bundlerをインストール**まで読み飛ばしてください。

```bash
ruby -v
```

### Homebrewのインストールを確認

Cloud9にデフォルトでインストールされているパッケージ管理システム「**Homebrew**」を使用していきます。

以下のコマンドでインストール済みのRubyのバージョンを確認します。

```bash
$ brew -v
```

コマンドが実行されると次のような画面になります。
```bash
$ brew -v
Homebrew >=2.2.0 (shallow or no git repository)
Homebrew/linuxbrew-core (git revision 09fd76; last commit 2020-11-06)
```

### rbenvをインストール

次に、Rubyのバージョンを簡単に切り替えられる`rbenv`をインストールします。

```bash
$ brew install rbenv
```

コマンドを実行後に、実際にrbenvがインストールされているかを確認します。

次のコマンドを入力して、インストールしたrbenvのバージョンを確認します

```bash
$ rbenv --version
```

コマンドを実行すると、次のようにバージョン情報が表示されます。

```bash
$ rbenv --version
rbenv 1.1.2

```

### rbenvにPATHを通す

rbenvコマンドを利用するために、rbenvにPATHを通します。

「PATHを通す」とは、コマンドの実行ファイルの場所を確認するために指定することです。

rbenvコマンドのPATHを通すために、次の3つのコマンドを用意しました。

```bash
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
$ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
```
まずは最初のコマンドです。

スクリプトを`.bash_profile`に追加します。

```console
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
```

`>> ~/.bash_profile`でスクリプトを`.bash_profile`に追加しました。


次に、２番めのコマンドを入力して実行します。

```console
$ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
```

このコマンドを追加することで、ターミナル起動時にrbenvを自動的に起動させます。

最後に、`source`というコマンドを使って追加した内容を反映します。

```console
$ source ~/.bash_profile
```

`.bash_profile`に追加した内容を反映できました。

これでrbenvコマンドを利用するのに必要なPATHが通りました。

### Rubyをインストール

Rubyをインストールする前に、インストールできるRubyのバージョンを確認します。

先ほどインストールしたrbenvを使って次のコマンドを入力してください。

```bash
$ rbenv install -l
```
コマンドを実行すると、最新の安定版のバージョンが一覧で表示されます。

```console
$ rbenv install -l
2.5.8
2.6.6
2.7.2
jruby-9.2.13.0
maglev-1.0.0
mruby-2.1.2
rbx-5.0
truffleruby-20.2.0
truffleruby+graalvm-20.2.0

Only latest stable releases for each Ruby implementation are shown.
Use 'rbenv install --list-all' to show all local versions.
```

※ インストール可能なrubyのバージョンを全て表示するには、上記の実行結果にあるように`rbenv install --list-all`というコマンドを実行します。

バージョン番号を見ると、執筆時点（2020年10月）の安定版の最新バージョンは「2.7.2」なので、2.7.2をインストールします。

参考：[Ruby ダウンロード](https://www.ruby-lang.org/ja/downloads/)

もし最新バージョンが表示されない場合は、rbenvとruby​​-buildを最新版にする必要があります。

参考：[rbenv Upgrading with Homebrew](https://github.com/rbenv/rbenv#upgrading-with-homebrew)

それでは、次のコマンドを入力してRuby 2.7.2をインストールします。

```bash
$ rbenv install 2.7.2
```

コマンドを実行するとインストールを開始します。インストール完了まで数分間かかることがあります。

これでRubyがインストールされました。

## Bundlerをインストール

Rubyをインストールしたら、次に**Bundler**をインストールします。

Rubyでは**Gem**というライブラリを使いパッケージを管理しています。

Gemコマンドで簡単にインストールやアンインストールができますが、複数のGemを使うとGem同士で依存関係が生まれ、バージョン違いによる不具合が出てきます。

そこで、BundlerでGemのそれぞれのバージョンを正確に追跡し管理して、Rubyプロジェクトに一貫した環境を提供します。

参考：
- [Bundler](https://bundler.io/)
- [RubyGems](https://rubygems.org/)

それではBundlerをインストールしましょう。以下のコマンドをCloud9のTerminalに入力します。

```bash
$ gem install bundler
```


## Ruby on Railsのバージョンを確認する

ここからはRailsのバージョンを確認していきます。

Cloud9のTerminalで以下のコマンドを実行してRailsのバージョンを確認しましょう。

```bash
$ rails -v
```

以下のようにデフォルトで指定されるRailsのバージョンが表示されます。

```bash
$ rails -v
Rails 5.0.0
```

`rails new`を実行する際にバージョンを指定しないとこのバージョンでアプリケーションが作成されます。

次に、インストールされているRailsのバージョンを確認しましょう。

以下のコマンドを実行して下さい。

```bash
$ gem list rails
```

以下のように表示されるので、**rails**の項目を確認しましょう。
「5.0.7.2」「5.0.0」がインストールされていることがわかるかと思います。

```bash
$ gem list rails

*** LOCAL GEMS ***

coffee-rails (4.2.2)
jquery-rails (4.4.0)
rails (5.0.7.2, 5.0.0)
rails-dom-testing (2.0.3)
rails-html-sanitizer (1.3.0)
sass-rails (5.0.7)
sprockets-rails (3.2.2)
```

ここで表示されているRailsのバージョンが本教材のRailsバージョンと同じであれば、このパートを読み飛ばしてください。


## Ruby on Railsのバージョンをインストールする

それではここからRailsのバージョンをインストールする方法を説明していきます。

以下のコマンドでRailsのバージョンをインストールすることができます。

`<version>`の部分には、インストールするバージョンを指定してください。

```bash
$ gem install rails -v <version>
```

次のように表示されていれば正常にインストールが完了しています。
以下の例では`6.0.0`を指定しています。

```bash
$ gem install rails -v <version>

//===略===

Installing ri documentation for actionmailbox-6.0.0
Parsing documentation for actiontext-6.0.0
Installing ri documentation for actiontext-6.0.0
Parsing documentation for railties-6.0.0
Installing ri documentation for railties-6.0.0
Parsing documentation for rails-6.0.0
Installing ri documentation for rails-6.0.0
Done installing documentation for zeitwerk, activesupport, erubi, actionview, actionpack, activemodel, activerecord, activejob, actionmailer, actioncable, mimemagic, marcel, activestorage, actionmailbox, actiontext, railties, rails after 13 seconds
17 gems installed
```

最後に以下のコマンドで先ほどインストールしたRailsのバージョンが追加されていることを確認しましょう。

```bash
$ gem list rails

*** LOCAL GEMS ***

coffee-rails (4.2.2)
jquery-rails (4.4.0)
rails (6.0.0, 5.0.7.2, 5.0.0)
rails-dom-testing (2.0.3)
rails-html-sanitizer (1.3.0)
sass-rails (5.0.7)
sprockets-rails (3.2.2)
```

以上でRuby、Ruby on Railsのバージョンに関する説明は終わりです。

教材とバージョンが異なると、思わぬエラーが発生する場合があります。教材と同じバージョンで進めることを推奨しています。


