> ここでは、`rails new`からサーバーを立ち上げ、Railsのデフォルトページを表示するところまでを記載しています。アプリ名など必要な部分は適切なものに変更してください。
>
> ここから教材

# 新規Railsプロジェクトの作成
このパートからRailsでWebアプリケーションを作成していきます。Ruby on Railsの開発環境は構築出来ている前提で進めていきます。

**本教材はRails5に対応する形で作成しています。Rails6には対応していませんのでご了承ください。**


## 本パートの目標物
本パートでは、ローカルサーバーを立ち上げてデフォルトのRailsページを表示するところまでやっていきます。

![image](https://i.gyazo.com/3ebe24e148a6a3e622ac0b9b8424325e.jpg)


## 目標物を作成するまでの流れ
1. ローカルにインストールされているRailsのバージョンの確認
2. 新規Railsアプリケーションの作成
3. Gemのインストール
4. ローカルサーバーを立ち上げる
5. デフォルトのRailsページを表示

では実際に進めてみましょう。


## 1. 新規Railsアプリケーションの作成
新規Railsアプリケーションを作成する前にローカルにインストールされているRailsのバージョンを確認しましょう。以下のコマンドをターミナル上で実行してください。

```
$ gem search ^rails$ -l
```

すると下記のような結果が表示されます。

```
$ gem search ^rails$ -l

*** LOCAL GEMS ***

rails (5.2.3, 5.2.1)
```

上記の結果だと、Rails5.2.1とRails5.2.3がインストールされていることがわかります。このインストールされているバージョンを使ってRailsアプリケーションを作成しましょう。


## 2. 新規Railsアプリケーションの作成
RailsでWebアプリケーションを新規作成するには、「rails new」コマンドを実行します。下記に実行例を示します。

**【例】**

```
$ rails new アプリケーション名
```

（**上記はあくまで実行例です。実際にコマンドを実行しないでください。**）

今回は「app-name」というアプリケーション名で作成したいので下記のコマンドを実行してください。

```
$ rails _5.2.3_ new app-name
```

> アプリ名は作成する教材に合わせて修正してください。

`rails`と`new`の間にバージョンを記載することで、Railsのバージョンを指定できます。ここではローカルにインストールしているRailsのバージョンを指定してください。今回のカリキュラムでは5.2.3のバージョンを指定しています。

上記のコマンドで「app-name」というディレクトリ（フォルダ）が作成されました。「cd」コマンドを使って移動したいディレクトリに移動します。

**【例】**

```
$ cd 移動したいディレクトリ名
```

「cd」コマンドはchange directory（ディレクトリを移動する）の略です。今回はapp-nameというディレクトリに移動したいので下記のコマンドを実行します。

```
$ cd app-name
```


## 3. Gemのインストール
新規アプリケーションを作成したら、次にGemをインストールします。

GemとはRuby用のライブラリを使うときに必要となるパッケージ管理ツールになります。

Railsでは Gemを使うことでRubyのライブラリ（機能のまとまり）をインストールして、0から機能を作らずに、簡単にアプリケーション開発を行う事ができます。Gemの1つとして例えば、認証機能が作れる「Devise」というものがあります。

ちなみにGemの正式名称は「RubyGems」です。Googleで検索するときも「RubyGems」とキーワード入力した方が、情報が探しやすくなります。

参考）[RubyGems.org | your community gem host](https://rubygems.org/)

それでは、Gemのインストールを行いましょう。以下のコマンドを実行してください。

```
$ bundle install
```

「bundle install」を実行すると、 Gemfileの内容に従いGemのインストールが行われます。（Gemfileはrails newコマンドでアプリケーションを作成したときに作成されます。）


## 4. ローカルサーバーを立ち上げる
ローカルサーバーを立ち上げるには以下のコマンド実行すればサーバーが立ち上がります。

```
$ bundle exec rails server
```

サーバーを起動させるコマンドは`rails server`に当たります。`rails s`と省略することもできます。

`bundle exec`を先頭につけているのは、現在のプロジェクト（今回で言うとapp-name)のGemを指定するためです。

`bundle exec`に関してもっと詳しく知りたい方は以下のリンクを参考にしてください。

参考）[bundle exec](https://bundler.io/v2.0/man/bundle-exec.1.html)

うまくサーバーが起動している場合、ターミナルが下記のように表示されています。

```
$ bundle exec rails server
=> Booting Puma
=> Rails 5.2.3 application starting in development 
=> Run `rails server -h` for more startup options
Puma starting in single mode...
* Version 3.12.1 (ruby 2.6.3-p62), codename: Llamas in Pajamas
* Min threads: 5, max threads: 5
* Environment: development
* Listening on tcp://localhost:3000
Use Ctrl-C to stop
```


## 5. デフォルトのRailsページを表示
サーバーを起動したら、ブラウザで http://localhost:3000/ にアクセスしてください。

**注意）** Cloud9の方はこちらのページを参考にデフォルトのRailsページを表示させてください。

参考）[Cloud9でページを表示する方法（Rails）](https://qiita.com/daijiro_maeyama/private/51fe7517639f11d634d3)

下記の画像のようにデフォルトのRailsページが表示されていれば、うまく動作しています。

![image](https://i.gyazo.com/3ebe24e148a6a3e622ac0b9b8424325e.jpg)


### sqlite3のエラーが出る場合
**（エラーは出ず、デフォルトのRailsページが表示された方は次のパートに進んで大丈夫です。）**

Railsのバージョン`5.2.3`を使っている場合は起きないのですが、それ以前のバージョンを使っているとsqlite3周りでエラーに遭遇する場合があります。

（SQLiteとはアプリケーションに組み込んで利用されるデータベースのことです。RailsはデフォルトのデータベースがSQLiteに設定されています。)

エラーメッセージは下記のようなものです。

> Puma caught this error: Error loading the 'sqlite3' Active Record adapter. Missing a gem it depends on? can't activate sqlite3 (~> 1.3.6), already activated sqlite3-1.4.0. Make sure all dependencies are added to Gemfile. (LoadError)

このエラーの対処方法を記載します。

Gemfileのsqlite3の箇所を以下のように編集してください。

```
kanban
└── Gemfile
```

```ruby
# Bundle edge Rails instead: gem 'rails', github: 'rails/rails'
gem 'rails', '~> 5.2.2'
# Use sqlite3 as the database for Active Record
gem 'sqlite3', '~>1.3.6' # この行に「, '~>1.3.6'」を追加する
# Use Puma as the app server
gem 'puma', '~> 3.11'
```

![image](https://camo.githubusercontent.com/25820619fddcaa9ad48e4ff3206ab07e23658921/68747470733a2f2f692e6779617a6f2e636f6d2f37643833623465373438643038373464616431643262383364313932616131332e706e67)

(上記の画像やコードのRailsのバージョンは`5.2.2`にっていますが、Railsのバージョンは5.1以上であれば問題ありません。)

sqlite3のバージョンを指定できたらGemのインストールを行いましょう。以下のコマンドを実行してください。

```
$ bundle install
```

`bundle install`を実行したら、再度サーバーを立ち上げてRailsのデフォルトページが表示されるか試してください。

以上で今回のパートは終了です。

お疲れさまでした。
