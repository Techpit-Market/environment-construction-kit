> ここでは、新規Djangoプロジェクトを作成し、Djangoのデフォルトページを表示するところまでを記載しています。プロジェクト名など必要な部分は適切なものに変更してください。
>
> ここから教材


# 新規Djangoプロジェクトの作成
このパートからDjangoでWebアプリケーションを作成していきます。Djangoの開発環境は構築出来ている前提で進めていきます。

**本教材はDjango2.2.7に対応する形で作成しています。Django3には対応していませんのでご了承ください。**


## 本パートの目標物
本パートでは、開発用サーバーを立ち上げてデフォルトのDjangoページを表示するところまでやっていきます。

![image](https://i.gyazo.com/be0e36c72604f732996e0fa8ec220d3d.png)


## 目標物を作成するまでの流れ
1. Djangoプロジェクトとは
2. 新規Djangoプロジェクトの作成
3. 開発用サーバーの起動

では実際に進めてみましょう。


## 1. Djangoプロジェクトとは
プロジェクトとは、データベースの設定などのDjango全体の設定群をまとめたひとつの単位です。

また、プロジェクトとは別にアプリケーションという単位が存在します。アプリケーションは実際のWebアプリケーションのことです。1つのDjangoプロジェクトには複数のアプリケーションを作成することができます。

プロジェクトとアプリケーションの違いについては、[公式ドキュメント](https://docs.djangoproject.com/ja/2.2/intro/tutorial01/)にも記述がありますので補足として引用します。

> プロジェクトとアプリケーションの違いとは何でしょうか？アプリケーションとは、実際に何らかの処理を行う Web アプリケーションを指します。例えばブログシステムや公開レコードのデータベース、単純な投票アプリといった具合です。プロジェクトとは、あるウェブサイト向けに設定とアプリケーションを集めたものです。一つのプロジェクトには複数のアプリケーションを入れられ ます。また、一つのアプリケーションは複数のプロジェクトで使えます。


## 2. 新規Djangoプロジェクトの作成
それでは、実際にプロジェクトを作成しましょう。

最初に、あらかじめDjangoのプロジェクトを格納するディレクトリ`project`を作って、その中に移動します。

```
$ mkdir project
$ cd project
```

> `project`には任意のプロジェクト名を入れてください。

次に下記コマンドでプロジェクトを作成します。

```
$ pipenv run django-admin startproject config .
```

`pipenv run`は「pipenvで作成した仮想環境上で」という意味です。`run`以降を`pipenv`の仮想環境上で実行します。

プロジェクトを作成するコマンドは`django-admin startproject <プロジェクト名> <作成するディレクトリ>`です。`<作成するディレクトリ>`は省略できますが、`.(ドット)`を指定することでカレントディレクトリ直下にプロジェクトを展開してくれるようになります。

また、ここでは`<プロジェクト名>`を`config`としています。本来であれば`project`などにすべきですが、実際のプロジェクト名には設定ファイルが集約されるので、`config`とすることで、設定ファイルが`config`内に作成されます。

> `project` には任意のプロジェクト名を入れてください。


## 作成されたファイルの解説
プロジェクトを作成することで、以下のようなディレクトリ構成になります。

```
project
├── config
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py
```

> `project` には任意のプロジェクト名を入れてください。


### configディレクトリについて
`config`ディレクトリには4つのファイルが存在します。

`config/__init__.py`は、Pythonにディレクトリを認識させるためのファイルです。`__init__.py`がディレクトリ内に存在しないと、そのディレクトリのファイルを参照できなくなります。特別なことがない限り、`__init__.py`は空のファイルとなります。

`config/settings.py`は、Djangoプロジェクト全体に関わる設定を記述するファイルです。データベースの設定などもこのファイルに記述します。

`config/urls.py`は、ルーティング（URLの設定）を記述するファイルです。プロジェクトを作成した段階で、自動的にadminページ（管理画面機能）のルーティングが設定されています。

`config/wsgi.py`は、WSGI（Web Server Gateway Interface）に関する設定を記述するファイルです。ざっくり言うと、サーバーに関する設定を記述します。ちなみにWSGIはウィズギーと読みます。


### manage.pyについて
`manage.py`は開発サーバーを起動したり、データベースのマイグレート（作成）をしたりする際の命令を行うためのファイルです。

以下のコマンドで、あらかじめ定義されたコマンドを実行できます。

```
$ python manage.py <コマンド名>
```


## 3. 開発用サーバーの起動
プロジェクトを作成すると、開発用のサーバーが起動できるようになります。早速起動してみましょう。

下記コマンドで開発サーバーを起動できます。

```
$ pipenv run python manage.py runserver
```

うまくサーバーが起動している場合、ターミナルに下記のような表示がされています。

```
$ pipenv run python manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 17 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.

November 23, 2019 - 01:28:51
Django version 2.2.7, using settings 'config.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

```
You have 17 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.
```

といったエラーが出るかと思いますが、一旦はスルーして大丈夫です。http://127.0.0.1:8000/ で開発サーバーにアクセスできます。ブラウザで開いてみましょう。

![image](https://i.gyazo.com/be0e36c72604f732996e0fa8ec220d3d.png)

上記のようなページが表示されていれば、無事にプロジェクトが作成できています！おめでとうございます🎉
