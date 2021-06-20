> ここでは、`rails new`からサーバーを立ち上げ、Railsのデフォルトページを表示するところまでを記載しています。アプリ名など必要な部分は適切なものに変更してください。
>
> ここから教材

# 新規Railsプロジェクトの作成（Rails6）
このパートからRailsでWebアプリケーションを作成していきます（Rails6の環境がある前提で解説します）。


## 本パートのゴール
今回の目標は「ローカルサーバーを立ち上げて、Railsのデフォルトページを表示する」ことです。

![image](https://i.gyazo.com/63fef1182934fdc07ffcbac00b03439c.png)


## ゴールまでの流れ
ゴールまでの手順は次のとおりです。

1. ローカルにインストールされたRailsのバージョンを確認
2. 新規Railsアプリケーションを作成
3. 作成したディレクトリに移動
4. ローカルサーバーを起動
5. Railsのデフォルトページを表示

それでは、実際にWebアプリケーションの作成を行いましょう。


## 1. ローカルにインストールされているRailsのバージョンの確認
新規Railsアプリケーションを作成する前に、ローカルにインストールされたRailsのバージョンを確認します。

ターミナル上で、次のコマンドを入力してください。

```console
gem search ^rails$ -l
```

コマンドを実行すると、次のような結果が表示されます。

```console
gem search ^rails$ -l

*** LOCAL GEMS ***

rails (6.0.3.7)
```

「Rails6.0.3.7」がインストールされていることがわかります。

表示されたバージョンを使って、Railsアプリケーションを作成します。


## 2. 新規Railsアプリケーションの作成
RailsでWebアプリケーションを新規作成します。

Webアプリケーションの新規作成では、**rails newコマンド**を入力します。

`rails new`コマンドでは命令文の最後に作成するアプリケーション名を指定します。

**【例】**

```console
rails new 作成するアプリケーション名
```

今回はRails6.0.3.7を使って「**〇〇**」という名前のアプリケーションを作成します。

次のコマンドを入力します。

```console
rails _6.0.3.7_ new 〇〇
```

> アプリ名は作成する教材に合わせて修正してください

命令文の`rails`と`new`の間にRailsのバージョンを入力すると、Railsのバージョンを指定できます（ここではローカルにある6.0.3.7を指定）。

`rails new`コマンドで「〇〇」というディレクトリ（フォルダ）が作成されました。


## 3. 作成したディレクトリに移動する
**cdコマンド**を使って、新たに作成した「〇〇」ディレクトリに移動します。

ちなみに「cd」は、change directory（ディレクトリを移動する）の略です。

ディレクトリ移動を行う命令文は、次の表現になります。

**【例】**

```console
cd 移動したいディレクトリ名
```

今回は「〇〇」ディレクトリに移動するため、次のコマンドを入力します。

```console
cd 〇〇
```

コマンドを実行すると、「〇〇」ディレクトリに移動します。


## 4. ローカルサーバーを起動
ローカルサーバーを立ち上げるには、次のコマンドを入力します。

```console
rails server
```

コマンドを実行するとサーバーが起動します（`rails s`と省略することも可能）。

うまくサーバーが起動すると、ターミナルで次のように表示されます。

```console
rails server
=> Booting Puma
=> Rails 6.0.3.2 application starting in development
=> Run `rails server --help` for more startup options
Puma starting in single mode...
* Version 4.3.5 (ruby 2.7.1-p83), codename: Mysterious Traveller
* Min threads: 5, max threads: 5
* Environment: development
* Listening on tcp://127.0.0.1:3000
* Listening on tcp://[::1]:3000
Use Ctrl-C to stop
```


## 5. Railsのデフォルトページを表示
ローカルサーバーを起動したら、ブラウザで「http://localhost:3000/ 」にアクセスします。

**注意）** Cloud9の方はこちらのページを参考にデフォルトのRailsページを表示させてください。

参考）[Cloud9でページを表示する方法（Rails）](https://qiita.com/daijiro_maeyama/private/51fe7517639f11d634d3)

次の画像のようにRailsのデフォルトページが表示されていれば、うまく動作しています。

![image](https://i.gyazo.com/63fef1182934fdc07ffcbac00b03439c.png)

以上で今回のパートは終了です。

お疲れさまでした。
