# 【Cloud9】バージョンの確認

このパートでは、RubyおよびRuby on Railsのバージョンを確認していきます。

なお、この教材ではRubyのバージョンは○○、Ruby on Railsのバージョンは○○を推奨しています。

> ○○に教材のバージョンを入れてください


## Rubyのバージョンを確認する

以下のURLからコンソールにサインインして、Cloud9を立ち上げましょう。

https://us-east-2.console.aws.amazon.com/console/

Cloud9上のTerminalを立ち上げて、以下のコマンドを実行してRubyのバージョンを確認しましょう。

```bash
ruby -v
```

以下のように数字が表示されます。

```bash
ruby -v
ruby 2.6.3p62 (2019-04-16 revision 67580) [x86_64-linux]
```

ここではRubyの環境が「**2.6.3**」であることがわかります。

Cloud9のRubyのバージョンが本教材のバージョンと同じであれば、「**Bundlerをインストール**」まで読み飛ばしてください。


## Rubyのバージョンを変更する

それではここからRubyのバージョンを変更していきます。

Rubyのバージョン管理ツールであるrvmを使います。

以下のコマンドでインストール済みのRubyのバージョンを確認します。

```bash
rvm list
```

実行結果は以下になります。

```bash
rvm list
=* ruby-2.6.3 [ x86_64 ]

# => - current
# =* - current && default
#  * - default
```

また、以下のコマンドでインストール可能なRubyのバージョンを一覧表示します。

```bash
rvm list known
```

実行結果で、自分のインストールしたいバージョンがあることを確認してください。

```bash
rvm list known

//====略====

# MRI Rubies
[ruby-]1.8.6[-p420]
[ruby-]1.8.7[-head] # security released on head
[ruby-]1.9.1[-p431]
[ruby-]1.9.2[-p330]
[ruby-]1.9.3[-p551]
[ruby-]2.0.0[-p648]
[ruby-]2.1[.10]
[ruby-]2.2[.10]
[ruby-]2.3[.8]
[ruby-]2.4[.6]
[ruby-]2.5[.5]
[ruby-]2.6[.3]
ruby-head

//====略====

```

ここでインストールしたいバージョンがない場合は、rvmのアップデートをおこなう必要があります。

アップデートをするには、以下のように`get`コマンドを実行します。

```bash
rvm get latest
```

```bash
rvm get latest

//====略====

Thanks for installing RVM 
Please consider donating to our open collective to help us maintain RVM.

  Donate: https://opencollective.com/rvm/donate


RVM reloaded!
```

インストールしたrvmのバージョンを確認しましょう。

```bash
rvm -v
rvm 1.29.10 (1.29.10) by Michal Papis, Piotr Kuczynski, Wayne E. Seguin [https://rvm.io]
```

次に、以下のコマンドを実行してRubyのバージョンをインストールします。

`<version>`の部分には、インストールするバージョンを指定してください。

```bash
rvm install <version>
```

以下のように表示されれば正常にインストールされています。

ここでは`2.7.2`を指定しています。

```bash
$ rvm install 2.7.2

//===略===

ruby-2.7.2 - #generating global wrappers.......
ruby-2.7.2 - #gemset created /home/ec2-user/.rvm/gems/ruby-2.7.0
ruby-2.7.2 - #importing gemsetfile /home/ec2-user/.rvm/gemsets/default.gems evaluated to empty gem list
ruby-2.7.2 - #generating default wrappers.......
```

以下のコマンドで使用するバージョンを指定しましょう。

```bash
$ rvm use <version>
```

最後に以下のコマンドで、先ほど指定したバージョンが表示されることを確認してください。

```bash
$ ruby -v
ruby 2.7.2p137 (2020-10-01 revision 5445e04352) [x86_64-linux]
```

以上でRubyのバージョン変更は終了です。


## Bundlerをインストール
Rubyをインストールしたら、次に**Bundler**をインストールします。

Rubyでは**Gem**というライブラリを使いパッケージを管理しています。

Gemコマンドで簡単にインストールやアンインストールができますが、複数のGemを使うとGem同士で依存関係が生まれ、バージョン違いによる不具合が出てきます。

そこで、BundlerでGemのそれぞれのバージョンを正確に追跡し管理して、Rubyプロジェクトに一貫した環境を提供します。

参考：
- [Bundler](https://bundler.io/)
- [RubyGems](https://rubygems.org/)

それではBundlerをインストールしましょう。以下のコマンドを入力します。

```bash
$ gem install bundler
```

コマンドを実行するとインストールが始まります。

インストールされたBlundlerのバージョンを確認しましょう。

次のコマンドを入力します。

```bash
$ bundler -v
```

コマンドの実行後、次のように表示されます。

```bash
$ bundler -v
Bundler version 2.1.4
```

「version 2.1.4」とバージョン情報が表示されました。

これでBlundlerがインストール済みであることを確認できました。


## yarnをインストール
次に**yarn**をインストールします。

yarnはJavaScriptのライブラリの利用に必要なパッケージマネージャです。

yarnと互換性のあるnpmというパッケージマネージャもあります。しかし、Rails6ではWebpackerが標準になったことにより、yarnが必要です。

それでは、yarnのインストールを行いましょう。

次のコマンドを入力します。

```bash
$ brew install yarn
```

Homebrewのコマンドを実行すると、yarnがインストールされます。

yarnが実際にインストールされたかを確認するために、次のコマンドを入力します。

```bash
$ yarn -v
```

コマンドを実行すると、次のように表示されます。

```bash
$ yarn -v
1.16.0
```

ここでは「`1.16.0`」と表示されました。バージョン情報が表示されていれば、yarnがインストールされたことが確認できます。

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


