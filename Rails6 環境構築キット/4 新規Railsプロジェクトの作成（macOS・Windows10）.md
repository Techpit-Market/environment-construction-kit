> ここでは、`rails new`からサーバーを立ち上げ、Railsのデフォルトページを表示するところまでを記載しています。
> 
> Railsはローカルにインストールしていることを前提としているため、`rails`コマンド実行時には`bundle exec`を付けています。
> 
> sqlite3以外のDBを使用する場合は`rails new`時にオプションを指定してください(MySQLの場合：`bundle exec rails new. -d mysql`)。
>
> 他にも必要なオプションがあれば適宜変更してください。
>
> ここから教材

# 新規Railsプロジェクトの作成（Rails6）
このパートからRailsでWebアプリケーションを作成していきます（Rails6の環境がある前提で解説します）。


## 本パートのゴール
今回の目標は「ローカルサーバーを立ち上げて、Railsのデフォルトページを表示する」ことです。

![image](https://i.gyazo.com/63fef1182934fdc07ffcbac00b03439c.png)

## 新規Railsアプリケーションの作成
RailsでWebアプリケーションを新規作成します。

Railsアプリケーションの新規作成では、**rails newコマンド**を入力します。

以下のコマンドを実行してください。

```console
bundle exec rails new .
```

コマンドを実行すると以下のようなメッセージが表示されます。

```
・
・
・
Overwrite {プロジェクトディレクトリのパス}/Gemfile? (enter "h" for help) [Ynaqdhm] 
```

「Gemfileを上書きしていいですか？」と聞かれているので、「yes」を入力して、エンターキーを押してください。

Railsプロジェクトを作成するために必要なGemがインストールされます。


## ローカルサーバーを起動
ローカルサーバーを立ち上げるには、次のコマンドを入力します。

```console
bundle exec rails server
```

コマンドを実行するとサーバーが起動します（`bundle exec rails s`と省略することも可能）。

うまくサーバーが起動すると、ターミナルで次のように表示されます。

```
=> Booting Puma
=> Rails 6.1.4.1 application starting in development 
=> Run `bin/rails server --help` for more startup options
Puma starting in single mode...
* Puma version: 5.5.2 (ruby 3.0.2-p107) ("Zawgyi")
*  Min threads: 5
*  Max threads: 5
*  Environment: development
*          PID: 46154
* Listening on http://127.0.0.1:3000
* Listening on http://[::1]:3000
Use Ctrl-C to stop
```

## Railsのデフォルトページを表示
ローカルサーバーを起動したら、ブラウザで「http://localhost:3000/ 」にアクセスします。

次の画像のようにRailsのデフォルトページが表示されていれば、うまく動作しています。

![image](https://i.gyazo.com/63fef1182934fdc07ffcbac00b03439c.png)

以上で今回のパートは終了です。

お疲れさまでした。
