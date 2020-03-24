> ここでは、`rails new`からサーバーを立ち上げ、Railsのデフォルトページを表示するところまでを記載しています。アプリ名など必要な部分は適切なものに変更してください。
>
> ここから教材

# 新規Railsプロジェクトの作成（Rails6）
このパートからRailsでWebアプリケーションを作成していきます。Ruby on Railsの開発環境は構築出来ている前提で進めていきます。


## 本パートの目標物
本パートでは、ローカルサーバーを立ち上げてデフォルトのRailsページを表示するところまでやっていきます。

![image](https://i.gyazo.com/4893a86db8a9158919ee82803412d418.png)


## 目標物を作成するまでの流れ
1. ローカルにインストールされているRailsのバージョンの確認
2. 新規Railsアプリケーションの作成
3. Gemのインストール
4. ローカルサーバーを立ち上げる
5. デフォルトのRailsページを表示

では実際に進めてみましょう。


## 1. ローカルにインストールされているRailsのバージョンの確認
新規Railsアプリケーションを作成する前にローカルにインストールされているRailsのバージョンを確認しましょう。以下のコマンドをターミナル上で実行してください。

```
$ gem search ^rails$ -l
```

すると下記のような結果が表示されます。

```
$ gem search ^rails$ -l


*** LOCAL GEMS ***

rails (6.0.2, 6.0.1, 5.2.4.1, 5.2.3, 5.2.2, 5.2.0, 5.1.6.1, 5.1.6)
```

上記の結果だと、Rails6.0.2やRails6.0.1がインストールされていることがわかります。このインストールされているバージョンを使ってRailsアプリケーションを作成しましょう。


## 2. 新規Railsアプリケーションの作成
RailsでWebアプリケーションを新規作成するには、「rails new」コマンドを実行します。下記に実行例を示します。

**【例】**

```
$ rails new アプリケーション名
```

（**上記はあくまで実行例です。実際にコマンドを実行しないでください。**）

今回は「app-name」というアプリケーション名で作成したいので下記のコマンドを実行してください。

```
$ rails _6.0.2_ new app-name
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
=> Rails 6.0.2.2 application starting in development 
=> Run `rails server --help` for more startup options
/Users/.rbenv/versions/2.7.0/lib/ruby/gems/2.7.0/gems/actionpack-6.0.2.2/lib/action_dispatch/middleware/stack.rb:37: warning: Using the last argument as keyword parameters is deprecated; maybe ** should be added to the call
/Users/.rbenv/versions/2.7.0/lib/ruby/gems/2.7.0/gems/actionpack-6.0.2.2/lib/action_dispatch/middleware/static.rb:110: warning: The called method `initialize' is defined here
Puma starting in single mode...
* Version 4.3.3 (ruby 2.7.0-p0), codename: Mysterious Traveller
* Min threads: 5, max threads: 5
* Environment: development
* Listening on tcp://127.0.0.1:3000
* Listening on tcp://[::1]:3000
Use Ctrl-C to stop
```


## 5. デフォルトのRailsページを表示
サーバーを起動したら、ブラウザで http://localhost:3000/ にアクセスしてください。

**注意）** Cloud9の方はこちらのページを参考にデフォルトのRailsページを表示させてください。

参考）[Cloud9でページを表示する方法（Rails）](https://qiita.com/daijiro_maeyama/private/51fe7517639f11d634d3)

下記の画像のようにデフォルトのRailsページが表示されていれば、うまく動作しています。

![image](https://i.gyazo.com/4893a86db8a9158919ee82803412d418.png)

以上で今回のパートは終了です。

お疲れさまでした。
