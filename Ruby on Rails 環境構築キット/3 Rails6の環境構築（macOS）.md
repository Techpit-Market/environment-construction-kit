> ここではmacOSにおけるRuby on Railsの環境構築方法を記載しています。対応バージョンは以下の通りです。
>
> - Ruby 2.7.0
> - Rails 6.0.2
>
> ここから教材

# Ruby on Railsの環境構築（macOS）
Webアプリケーションを開発するための環境を構築します。

今回、環境構築するのは、Ruby on Railsです。

もし既にお手元のPCにRuby on Railsの環境があれば、このパートは読み飛ばしても大丈夫です。

**注意）今回のパートで環境構築する対応のPCはMacになります。**


## Homebrewをインストール
Homebrewとは、ソフトウェアの導入を単純化するmacOSのパッケージ管理システムです。

下記のリンクからHomebrewをインストールします。

[Homebrew](https://brew.sh/index_ja.html)

上記のリンクにアクセスすると下記のような画面が表示されるので「インストール」と記載されているスクリプトをターミナル上で実行してください。

![image](https://i.gyazo.com/069a774cc3f47cab32d7bed52e9b9bbf.png)

スクリプトを実行するとインストールが開始します。インストールには数分~10分程かかります。途中何度かパスワードを要求されるのでご自身のPCのパスワードを入力してください。


## Homebrewがインストールされているか確認
Homebrewをインストールしたら、Homebrewがインストールされているか確認します。以下のコマンドを実行してください。（コマンドを実行する際に`$`は含めないでください。行の頭に「$」を表示するスタイルを使って、その例がコマンドラインであることを示しています。）

```
$ brew -v
Homebrew 2.1.16
Homebrew/homebrew-core (git revision 1e525; last commit 2019-11-11)
Homebrew/homebrew-cask (git revision 8767c; last commit 2019-11-11)
```

上記のように`2.1.16`のようなバージョンが表示されればHomebrewはインストールされています。

（筆者のPCでは`2.1.16`と表示されていますが、インストールした時期によってバージョンは違います。なので`2.1.16`ではなく、`2.1.17`など別のバージョンが表示されることもありますが、バージョン(数字)が表示されていればインストールされています。)


## rbenvをインストール
rbenvをインストールします。rbenvをインストールすることでrubyのバージョンの切り替えが容易にできるようになります。 それでは下記のコマンドを実行してください。

```
$ brew install rbenv
```

上記のコマンドを実行したらrbenvがインストールされているか確認します。以下のコマンドを実行してバージョンの情報が表示されていればインストールされています。

```
$ rbenv --version
rbenv 1.1.2
```


## rbenvにPATHを通す
rbenvコマンドを利用するために、rbenvにPATHを通します。PATHを通すとは、コマンド実行ファイルを探しに行くパスを追加することです。

参考）[PATHを通すとは？（Mac OS X）](https://qiita.com/soarflat/items/09be6ab9cd91d366bf71)

それでは、下記のコマンドを1つずつ実行してください。

```
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
$ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
$ source ~/.bash_profile
```

`>> ~/.bash_profile`でスクリプトを`.bash_profile`に追加しています。

また最後に`source`コマンドを使うことで`.bash_profile`に追加した内容を反映できます。


## Rubyをインストール
まずRubyをインストールする前に、先ほどインストールしたrbenvを使ってインストール可能なrubyのバージョンを確認します。

以下のコマンドを実行してください。

```
$ rbenv install -l
```

すると下記のようにrubyのインストール可能なバージョンの一覧が表示されます。

```
Available versions:
  1.8.5-p52
  1.8.5-p113
  1.8.5-p114
  ---中略---
  2.5.1
  2.5.2
  2.5.3
  2.5.4
  2.5.5
  2.5.6
  2.5.7
  2.6.0-dev
  2.6.0-preview1
  2.6.0-preview2
  2.6.0-preview3
  2.6.0-rc1
  2.6.0-rc2
  2.6.0
  2.6.1
  2.6.2
  2.6.3
  2.6.4
  2.6.5
  2.7.0-dev
  2.7.0-preview1
  2.7.0-preview2
  2.7.0-preview3
  2.7.0-rc1
  2.7.0-rc2
  2.7.0
  2.8.0-dev
  .
  .
  .
```

現在の最新のバージョンは2.7.0になるので、2.7.0のバージョンをインストールします。（2020年1月時点）

2.7.0のバージョンが表示されない場合は、rbenvとruby​​-buildを最新にアップグレードする必要があります。

参考：[rbenv Upgrading with Homebrew](https://github.com/rbenv/rbenv#upgrading-with-homebrew)

それでは、以下のコマンドを実行してください。(インストール完了まで数分かかることがあります。)

```
$ rbenv install 2.7.0
```

インストールが完了したら、PC（サーバー）内で共通に使うためにグローバルで利用するバージョンを設定します。

```
$ rbenv global 2.7.0
```

プロジェクトごとにRubyのバージョンを指定する場合は`global`ではなく`local`を使います。

次にRubyのバージョン情報を確認します。

```
$ ruby -v
ruby 2.7.0p0 (2019-12-25 revision 647ee6f091) [x86_64-darwin19]
```


## Bundlerをインストール
Bundlerとは、必要なGemとバージョンを正確に追跡およびインストールすることにより、Rubyプロジェクトに一貫した環境を提供します。GemとはRuby用のライブラリを使うときに必要となるパッケージ管理ツールのことです。

参考）
- [Bundler](https://bundler.io/)
- [RubyGems](https://rubygems.org/)

それではBundlerをインストールしましょう。以下のコマンドを実行してください。

```
$ gem install bundler
```

上記のコマンドを実行したらbundlerのバージョンを確認します。バージョン情報が表示されていればインストールされています。

```
$ bundler -v
Bundler version 1.17.2
```


## yarn をインストール
yarnとは、JavaScriptのライブラリを使うときに必要になるパッケージマネージャです。

Rails6では、WebpackerがデフォルトのJavaScriptのコンパイラになるため、yarnが必要になります。yarnと似たようなパッケージマネージャにnpmがありますが、Railsは標準でyarnを利用しているため今回はそれに準拠してyarnをインストールします。

それでは、yarnのインストールを行いましょう。以下のコマンドを実行してください。

```
$ brew install yarn
```

yarnをインストールすることで、yarnコマンドを使うことができます。

上記のコマンドを実行したらyarnがインストールされているか確認します。以下のコマンドを実行してバージョンの情報が表示されていればインストールされています。

```
$ yarn -v
1.19.1
```


## Railsをインストール
最後にRailsをインストールします。以下のコマンドを実行してください。(インストール完了まで数分かかることがあります。)

```
$ gem install rails -v 6.0.2
```

`-v バージョン`を記載することでバージョンを指定してRailsをインストールできます。今回の場合`6.0.2`のバージョンをインストールしています。

実行ができたら以下のコマンドでRailsのバージョンを確認します。

```
$ rails -v
Rails 6.0.2
```

以上でRuby on Railsをインストールできました。

お疲れ様でした。
