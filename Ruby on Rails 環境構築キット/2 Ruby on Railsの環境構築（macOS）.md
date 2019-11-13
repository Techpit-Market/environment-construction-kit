> ここではmacOSにおけるRuby on Railsの環境構築方法を記載しています。対応バージョンは以下の通りです。
>
> - Ruby 2.6.5
> - Rails 5.2.3
>
> Rails6を使う場合はバージョン等を編集してください。
>
> ここから教材

# Ruby on Railsの環境構築（macOS）
Webアプリケーションを開発するための環境を構築します。

今回、環境構築するのは、Ruby on Railsです。

もし既にお手元のPCにRuby on Railsの環境があれば、このパートは読み飛ばしても大丈夫です。

**注意）今回のパートで環境構築する対応のPCはMacになります。**


## Homebrewをインストール
Homebrewとは、ソフトウェアの導入を単純化するmacOSのパッケージ管理システムです。

下記のURLからHomebrewをインストールします。

[Homebrew](https://brew.sh/index_ja.html)

上記のリンクにアクセスすると下記のような画面が表示されるので「インストール」と記載されているスクリプトをターミナル上で実行してください。

![image](https://i.gyazo.com/069a774cc3f47cab32d7bed52e9b9bbf.png)

スクリプトを実行するとインストールが開始します。インストールには数分~10分程かかります。途中何度かパスワードを要求されるのでご自身のPCのパスワードを入力してください。


## Homebrewがインストールされているか確認
Homebrewをインストールしたら、Homebrewがインストールされているか確認します。以下のコマンドを実行してください。（コマンドを実行する際に`$`は含めないでください。行の頭に「$」を表示するスタイルを使って、その例がコマンドラインであることを示しています。） 

```
$ Homebrew 2.1.15
Homebrew/homebrew-core (git revision bb953; last commit 2019-10-19)
Homebrew/homebrew-cask (git revision 2d83; last commit 2019-10-19)
```

上記のように`2.1.15`のようなバージョンが表示されればHomebrewはインストールされています。

（筆者のPCでは`2.1.15`と表示されていますが、インストールした時期によってバージョンは違います。なので`2.1.15`ではなく、`2.1.14`など別のバージョンが表示されることもありますが、バージョン(数字)が表示されていればインストールされています。)


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
  2.5.0
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
  .
  .
  .
```

現在の最新のバージョンは2.6.5になるので、2.6.5のバージョンをインストールします。（2019年11月時点）

2.6.5のバージョンが表示されない場合は、rbenvとruby​​-buildを最新にアップグレードする必要があります。

参考：[rbenv Upgrading with Homebrew](https://github.com/rbenv/rbenv#upgrading-with-homebrew)

それでは、以下のコマンドを実行してください。(インストール完了まで数分かかることがあります。)

```
$ rbenv install 2.6.5
```

インストールが完了したら、PC（サーバー）内で共通に使うためにグローバルで利用するバージョンを設定します。

```
$ rbenv global 2.6.5
```

次にRubyのバージョン情報を確認します。

```
$ ruby -v
ruby 2.6.5p114 (2019-10-01 revision 67812) [x86_64-darwin19]
```


## Bundlerをインストールする
Bundlerとは、必要なgemとバージョンを正確に追跡およびインストールすることにより、Rubyプロジェクトに一貫した環境を提供します。

参考）[Bundler](https://bundler.io/)

それではBundlerをインストールしましょう。以下のコマンドを実行してください。

```
$ gem install bundler
```

上記のコマンドを実行したらbundlerのバージョンを確認します。バージョン情報が表示されていればインストールされています。

```
$ bundler -v
Bundler version 1.17.2
```


## Railsをインストールする
最後にRailsをインストールします。以下のコマンドを実行してください。(インストール完了まで数分かかることがあります。)

```
$ gem install rails -v 5.2.3
```

`-v バージョン`を記載することでバージョンを指定してRailsをインストールできます。今回の場合`5.2.3`のバージョンをインストールしています。

実行ができたら以下のコマンドでRailsのバージョンを確認します。

```
$ rails -v
Rails 5.2.3
```

以上でRuby on Railsをインストールできました。

お疲れ様でした。


### Railsのバージョンのダウングレード方法 
**ここでは、Rails6.0.0をインストールしていて、Rails5.2.3を使いたい場合、どのようにRailsのバージョンをダウングレードするか記載します。ダウングレードする必要がなければ読み飛ばしてください。**

まず今のRailsのバージョンを確認してください。

```
$ rails -v
Rails 6.0.0
```

次にRailsをアンインストールします。以下のコマンドを実行してください。

```
$ gem uninstall rails
Successfully uninstalled rails-6.0.0
```

上記のコマンドだけでは、まだRailsはアンインストールできていません。`railties`というRailsのコアライブラリをアンインストールする必要があります。

次に以下のコマンドを実行してください。

```
$ gem uninstall railties -v '6.0.0'
```

上記のコマンドを実行すると以下のような結果が表示されます。

```
Removing rails
Successfully uninstalled railties-6.0.0
```

Railsのバージョンの確認のコマンドを実行しても、`command not found`と表示されます。

```
$ rails -v
rbenv: rails: command not found
```

Railsをアンインストールしたら、使いたいRailsのバージョンをインストールをします。(今回の場合は5.2.3）以下のコマンドを実行してください。

```
$ gem install rails -v 5.2.3
```

実行ができたら以下のコマンドでRailsのバージョンを確認します。

```
$ rails -v
Rails 5.2.3
```

以上でRuby on Railsをダウングレードができました。

お疲れ様でした。
