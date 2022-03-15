> ここではmacOSにおけるRuby on Railsの環境構築方法を記載しています。対応バージョンは以下の通りです。
>
> - Ruby 2.7.2
>   - https://www.ruby-lang.org/ja/downloads/
> - Rails 6.0.3.7
>   - https://rubygems.org/gems/rails/versions
>
> ここから教材


# Ruby on Railsの環境構築（macOS）
Webアプリケーションを開発する環境を構築します。

今回は**Ruby on Rails 6**系の環境構築を行います。

すでにRuby on Rails 6系の環境が用意されていれば、この回を読み飛ばしてもかまいません。

**（注：本教材での環境構築はMacで行っています）**


## Homebrewをインストール
ソフトウェアの導入を簡単にするため、macOS用のパッケージ管理システムである**Homebrew**をインストールします。

次のリンク先からHomebrewをインストールします。

[Homebrew](https://brew.sh/index_ja.html)

リンク先にアクセスすると次のページが表示されます。

![image](https://i.gyazo.com/069a774cc3f47cab32d7bed52e9b9bbf.png)

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
Homebrew 2.5.6
Homebrew/homebrew-core (git revision 062ea; last commit 2020-10-14)
Homebrew/homebrew-cask (git revision c25fe8; last commit 2020-10-14)
```

「Homebrew 2.5.6」とバージョンが表示され、Homebrewがインストールされたことが確認できました。

（執筆時は「2.5.6」と表示されましたが、「2.5.7」などと表示されると最新版がインストールされたことになります)


## rbenvをインストール
次に、Rubyのバージョンを簡単に切り替えられる**rbenv**をインストールします。

それでは、ターミナルで次のコマンドを入力して実行してください。

```console
brew install rbenv
```

コマンドを実行後に、実際にrbenvがインストールされているかを確認します。

次のコマンドを入力して、インストールしたrbenvのバージョンを確認します。

```console
rbenv --version
```

コマンドを実行すると、次のようにバージョン情報が表示されます。

```console
rbenv --version
rbenv 1.1.2
```

この表示では「`rbenv 1.1.2`」とバージョン情報が表示されています。

rbenvがインストールされたことを確認できました。


## rbenvにPATHを通す
rbenvコマンドを利用するために、rbenvに**PATHを通します**。

「PATHを通す」とは、コマンドの実行ファイルの場所を確認するために指定することです。

参考：[PATHを通すとは？（Mac OS X）](https://qiita.com/soarflat/items/09be6ab9cd91d366bf71)

rbenvコマンドのPATHを通すために、次の3つのコマンドを用意しました。

```console
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
source ~/.bash_profile
```

これらのコマンドを１行ずつ入力して、実行します。

まずは最初のコマンドです。

スクリプトを`.bash_profile`に追加します。

```console
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
```

`>> ~/.bash_profile`でスクリプトを`.bash_profile`に追加しました。


次に、２番めのコマンドを入力して実行します。

```console
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
```

このコマンドを追加することで、ターミナル起動時にrbenvを自動的に起動させます。

最後に、`source`というコマンドを使って追加した内容を反映します。

```console
source ~/.bash_profile
```

`.bash_profile`に追加した内容を反映できました。

これでrbenvコマンドを利用するのに必要なPATHが通りました。


## Rubyをインストール
次に**Ruby**をインストールします。

Rubyをインストールする前に、インストールできるRubyのバージョンを確認します。

先ほどインストールしたrbenvを使って次のコマンドを入力してください。

```console
rbenv install -l
```

コマンドを実行すると、最新の安定版のバージョンが一覧で表示されます。

```console
rbenv install -l
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

※ インストール可能なrubyのバージョンを全て表示するには、上記の実行結果にあるように`rbenv install --list-all`というコマンドを実行します

バージョン番号を見ると、執筆時点（2020年10月）の安定版の最新バージョンは「2.7.2」なので、2.7.2をインストールします。

参考：[Ruby ダウンロード](https://www.ruby-lang.org/ja/downloads/)

もし最新バージョンが表示されない場合は、rbenvとruby​​-buildを最新版にする必要があります。

参考：[rbenv Upgrading with Homebrew](https://github.com/rbenv/rbenv#upgrading-with-homebrew)

それでは、次のコマンドを入力してRuby 2.7.2をインストールします。

```console
rbenv install 2.7.2
```

コマンドを実行するとインストールを開始します。インストール完了まで数分間かかることがあります。

これでRubyがインストールされました。


## ローカルで使うRubyのバージョンを指定
さらにローカルで使うRubyのバージョンを指定するために、以下のコマンドを実行します。

```console
rbenv local 2.7.2
```

これでローカルでRubyの2.7.1のバージョンが使用されます。

このように`local`を使うと、プロジェクトごとにRubyのバージョンを指定できます。

PC（サーバー）内で同じバージョンを共通して使う場合は、`local`ではなく`global`を使います。


次に、Rubyのバージョン情報を確認します。次のコマンドを入力します。

```console
ruby -v
```

コマンドを実行すると、次のようにバージョンが表示されます。

```console
ruby -v
ruby 2.7.2p137 (2020-10-01 revision 5445e04352) [x86_64-darwin19]
```

指定した「2.7.2」と表示されました。これで指定したRubyのバージョンが確認できました。


## Bundlerをインストール
Rubyをインストールしたら、次に**Bundler**をインストールします。

Rubyでは**Gem**というライブラリを使いパッケージを管理しています。

Gemコマンドで簡単にインストールやアンインストールができますが、複数のGemを使うとGem同士で依存関係が生まれ、バージョン違いによる不具合が出てきます。

そこで、BundlerでGemのそれぞれのバージョンを正確に追跡し管理して、Rubyプロジェクトに一貫した環境を提供します。

参考：
- [Bundler](https://bundler.io/)
- [RubyGems](https://rubygems.org/)

それではBundlerをインストールしましょう。以下のコマンドを入力します。

```console
gem install bundler
```

コマンドを実行するとインストールが始まります。

インストールされたBlundlerのバージョンを確認しましょう。

次のコマンドを入力します。

```console
bundler -v
```

コマンドの実行後、次のように表示されます。

```console
bundler -v
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

```console
brew install yarn
```

Homebrewのコマンドを実行すると、yarnがインストールされます。

yarnが実際にインストールされたかを確認するために、次のコマンドを入力します。

```console
yarn -v
```

コマンドを実行すると、次のように表示されます。

```console
yarn -v
1.16.0
```

ここでは「`1.16.0`」と表示されました。バージョン情報が表示されていれば、yarnがインストールされたことが確認できます。


## Railsをインストール
いよいよ、Railsをインストールします。

Railsのインストール時に「`-v バージョン番号`」とバージョンを指定してインストールできます。

今回はバージョン「`6.0.3.7`」をインストールします。

参考：[railsの全バージョン履歴](https://rubygems.org/gems/rails/versions)

次のコマンドを入力します。

```console
gem install rails -v 6.0.3.7
```

コマンドを実行すると、インストールを開始します。インストールの完了までに数分かかることがあります。


## Railsのバージョンを確認

Railsをインストールしたら、Railsのバージョンを確認するために次のコマンドを入力します。

```console
rails -v
```

コマンドを実行すると、次の画面が表示されます。

```console
rails -v
Rails 6.0.3.7
```

「`Rails 6.0.3.7`」と表示されました。

これで無事にRuby on Railsのインストールが完了しました。

以上でRuby on Railsをインストールできました。

お疲れ様でした。
