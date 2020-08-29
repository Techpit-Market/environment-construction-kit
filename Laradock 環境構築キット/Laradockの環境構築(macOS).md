> ここではmacOSにおけるPHP/Laravel(Laradock)の環境構築方法を記載しています。  
> Dockerはインストール済みであることを前提としています。  
> 起動させるコンテナは`workspace`, `php-fpm`, `nginx`, `postgres`としていますが、教材に合わせて置き換える等してください。  
> `app-name`となっている箇所は、今回作成するアプリケーション名に置き換えてください。
>
> ここから教材

# Laradockの環境構築（macOS）
このパートでは、Laradockをインストールして、Laravelの開発環境を構築します。

Laradockとは、LaravelのプロジェクトをDocker上で動作させるための環境です。

Laravelの実行にはPHPやnginx, MySQLなどのデータベース管理システムなど、いくつものプログラムやライブラリが必要になりますが、LaradockはLaravelの環境を構築するために必要なものを一つにまとめてくれているので、簡単に環境構築ができます。

## Laradockのインストール
まず、Laradockをインストールするディレクトリを作成します。
任意のディレクトリ配下に`app-name`ディレクトリを作成してください。

```
$ mkdir app-name
```

次に`cd`コマンドで作成したディレクトリに移動してください。

```
$ cd app-name
```

`app-name`ディレクトリに移動したら、Laradockをインストールします。
インストールには`git clone`コマンドを実行して、Laradockリポジトリから複製します。
以下のコマンドを実行してください。

```
$ git clone https://github.com/Laradock/laradock.git
```

実行すると、以下のようなメッセージが表示されます。

```
Cloning into 'laradock'...

(略)

Resolving deltas: 100% (5816/5816), done.
```

完了すると、`laradock`というディレクトリが作成されます。

```
app-name
└── laradock
```

## 環境設定ファイルの作成
Laradockの環境設定を記述する`.env`ファイルを作成します。

Laradockには`.env`ファイルの雛形である`env-example`ファイルが用意されているので、`env-example`ファイルを元に作成します。

まず、先ほど作成した`laradock`ディレクトリに移動しましょう。以下のコマンドを実行してください。

```
$ cd laradock
```

移動できたら、`cp`コマンドを用いて、`env-example`ファイルをコピーしたファイル`.env`を作成します。

```
$ cp env-example .env
```

## .envファイルの編集
> 設定は作成するアプリに合わせて変更してください。
>
> 本キットでは、`APP_CODE_PATH_HOST`、`DATA_PATH_HOST`、`COMPOSE_PROJECT_NAME`を編集します。
> 追加する場合は、追加する項目の説明と今回は何を設定するのかの説明を記載してください。
>
> ここから教材


今回は以下の設定を変更します。

|設定|説明|
|---|---|
|DATA_PATH_HOST|データベースのデータの保存場所を指定|
|COMPOSE_PROJECT_NAME|コンテナ名のプレフィックス(先頭に付ける名前)を指定|

コンテナとはDocker上で動くサービス(PHP, nginxなど)の単位のことです。

それではエディタを使って`.env`ファイルを編集します。

```diff
###########################################################
###################### General Setup ######################
###########################################################

### Paths #################################################

# Point to the path of your applications code on your host
APP_CODE_PATH_HOST=../

# Point to where the `APP_CODE_PATH_HOST` should be in the container
APP_CODE_PATH_CONTAINER=/var/www

# You may add flags to the path `:cached`, `:delegated`. When using Docker Sync add `:nocopy`
APP_CODE_CONTAINER_FLAG=:cached

# Choose storage path on your machine. For all storage systems
- DATA_PATH_HOST=~/.laradock/data
+ DATA_PATH_HOST=../data

### Drivers ################################################

# All volumes driver
VOLUMES_DRIVER=local

# All Networks driver
NETWORKS_DRIVER=bridge

### Docker compose files ##################################

# Select which docker-compose files to include. If using docker-sync append `:docker-compose.sync.yml` at the end
COMPOSE_FILE=docker-compose.yml

# Change the separator from : to ; on Windows
COMPOSE_PATH_SEPARATOR=:

# Define the prefix of container names. This is useful if you have multiple projects that use laradock to have separate containers per project.
- COMPOSE_PROJECT_NAME=laradock
+ COMPOSE_PROJECT_NAME=app-name

(略)
```

編集した内容を説明します。

```diff
# Choose storage path on your machine. For all storage systems
- DATA_PATH_HOST=~/.laradock/data
+ DATA_PATH_HOST=../data
```

データベースは`app-name/data`に保存することとするので、こちらも`laradock`ディレクトリからの相対パスで指定します。

`app-name/data`ディレクトリは、この後おこなうコンテナの起動時に作成されます。

```diff
# Define the prefix of container names. This is useful if you have multiple projects that use laradock to have separate containers per project.
- COMPOSE_PROJECT_NAME=laradock
+ COMPOSE_PROJECT_NAME=app-name
```

デフォルトではカレントディレクトリである`laradock`ディレクトリが指定されていますが、他のプロジェクトでLaradockを使用する場合、コンテナ名が重複してしまうとデータが混在する可能性があります。
プロジェクト名などの一意の名前に変更しておくことで、トラブルを防ぐことができます。

今回は`app-name`という名前に変更します。

## PostgreSQLのバージョンの指定
> 本キットでは`postgres`を使用します。
> MySQLなど、他のDBを使用する場合は置き換えて執筆してください。  
> また、`Dockerfile`の内容はlaradockのバージョンで異なる場合があるので注意してください。
>
> ここから教材

PostgreSQLとはデータベース管理システムの一つです。

本教材ではPostgreSQLのバージョンを11.6に指定して使用します。

バージョンの指定は`app-name/laradock/postgres`ディレクトリにある`Dockerfile`を編集します。

```
app-name
└── laradock
    └── postgres
        └── Dockerfile
```

`Dockerfile`を開いたら、1行目を以下のように編集してください。

```diff
- ARG POSTGRES_VERSION=alpine
+ ARG POSTGRES_VERSION=11.6
```

`alpine`となっているところを`11.6`と編集してください。

## Dockerを使って開発環境を起動する
> 起動完了のメッセージは起動するコンテナにより、置き換える等してください。
>
> ここから教材

今回は以下のコンテナを起動します。

|コンテナ|説明|
|---|---|
|workspace|Laravelでの開発に必要なツールを提供|
|php-fpm|サーバー上でPHPを実行する仕組みを提供|
|nginx|Webサーバー|
|postgres|データベース管理システム|

それではDockerを使って開発環境を起動しましょう。

`laradock`ディレクトリで以下のコマンドを実行してください。

```
$ docker-compose up -d workspace php-fpm nginx postgres
```

コマンドの意味は以下の通りです。

|コマンド|説明|
|---|---|
|docker-compose|複数のコンテナを同時に取り扱うDocker Composeという機能を使うためのコマンド|
|up|Docker Composeでコンテナを起動するときに使うコマンド|
|-d|コンテナをバックグランドで起動させるオプションで、起動後もターミナルの操作ができる|

コマンドを実行すると、各コンテナのソフトウェア本体(Dockerイメージ)をダウンロードします。

ダウンロードに時間がかかるため、初回のみコンテナの起動に数分かかります。

最後に以下のメッセージが表示されたら、コンテナの起動は成功です。

```
Creating laravel-ci_docker-in-docker_1 ... done
Creating laravel-ci_workspace_1        ... done
Creating laravel-ci_php-fpm_1          ... done
Creating laravel-ci_nginx_1            ... done
Creating laravel-ci_porstgres_1        ... done
```

もし、この5つのメッセージが表示されなかったら、もう一度`docker-compose up -d workspace php-fpm nginx postgres`を実行してください。

コンテナの起動が完了したら、今度はブラウザを起動し、アドレスバーにlocalhostと入力してください。

<img width="705" alt="" src="https://user-images.githubusercontent.com/25563739/89804619-6294e780-db6f-11ea-9f6b-0eef650fca1e.png">

上記のような画面が表示がされたら、起動成功です。

`404 Not Found`とエラーが表示されますが、Dockerで開発環境が起動できたことは分かりますので、現時点では問題ありません。

以上で、Laradockのインストールは完了です。

## Laravelのインストール

Laradockのインストールが完了したら、続いてLaravelのインストールをおこないます。

最初にworkspaceに入ります。

```
$ docker-compose exec workspace /bin/bash
```

以下のように表示され、workspace内でコマンドが実行できるようになります。

```
root@071c6db8cc60:/var/www#
```

次にLaravelをインストールします。以下のコマンドを実行してください。

```
# composer create-project laravel/laravel laravel-app-name
```

コマンドの意味は以下の通りです。

|コマンド|説明|
|---|---|
|composer|ライブラリの管理ツールであるcomposerを使うためのコマンド|
|create-project {パッケージ} {ディレクトリ}|指定したパッケージを指定したディレクトリへインストールするためのコマンド|

最後に以下のようなメッセージが出力されれば、インストール完了です。

```
Package manifest generated successfully.
48 packages you are using are looking for funding.
Use the `composer fund` command to find out more!
> @php artisan key:generate --ansi
Application key set successfully.
```

Laravelのインストールが完了したら、workspaceを抜けます。以下のコマンドを実行してください。

```
# exit
```

次に`.env`を編集し、先程インストールしたLaravelアプリケーションの場所を指定します。

エディタを使用して`.env`を開き、以下のように編集してください。

```diff
###########################################################
###################### General Setup ######################
###########################################################

### Paths #################################################

# Point to the path of your applications code on your host
- APP_CODE_PATH_HOST=../
+ APP_CODE_PATH_HOST=../laravel-app-name

(略)
```

編集した内容を説明します。

```diff
# Point to the path of your applications code on your host
- APP_CODE_PATH_HOST=../
+ APP_CODE_PATH_HOST=../laravel-app-name
```

`APP_CODE_PATH_HOST`はLaravelアプリケーションの場所を指定します。

今回はLaravelをインストールしたディレクトリである`laravel-app-name`を指定しました。

`.env`を保存したら、Dockerを再起動します。

`laradock`ディレクトリで以下のコマンドを実行してください。

```
$ docker-compose up -d workspace php-fpm nginx postgres
```

以下のメッセージが表示されたら、コンテナの起動は成功です。

```
Creating laravel-ci_docker-in-docker_1 ... done
Creating laravel-ci_workspace_1        ... done
Creating laravel-ci_php-fpm_1          ... done
Creating laravel-ci_nginx_1            ... done
Creating laravel-ci_porstgres_1        ... done
```

もし、この5つのメッセージが表示されなかったら、もう一度`docker-compose up -d workspace php-fpm nginx postgres`を実行してください。

コンテナの再起動が完了したら、再度ブラウザでlocalhostにアクセスしてください。

<img width="705" alt="" src="https://user-images.githubusercontent.com/25563739/91637183-8d24e280-ea41-11ea-8b6e-567d20f26c51.png">

上記のような画面が表示がされたら、Laravelの開発環境の準備は完了です。
