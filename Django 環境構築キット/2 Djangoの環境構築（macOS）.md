> ここではmacOSにおけるDjangoの環境構築方法を記載しています。対応バージョンは以下の通りです。
>
> - [Python 3.8.0](https://www.python.org/downloads/release/python-380/)
> - [Django 2.2.7](https://www.djangoproject.com/download/)
>
> Django3を使う場合はバージョン等を編集してください。
>
> ここから教材


# Djangoの環境構築（macOS）
Webアプリケーションを開発するための環境を構築します。

今回、環境構築するのは、Djangoです。

もし既にお手元のPCにDjangoの環境があれば、このパートは読み飛ばしても大丈夫です。

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


## pyenvのインストール
pyenvをインストールします。pyenvをインストールすることでPythonのバージョンの切り替えが容易にできるようになります。それでは下記のコマンドを実行してください。

```
$ brew install pyenv
```

上記のコマンドを実行したらpyenvがインストールされているか確認します。以下のコマンドを実行してバージョンの情報が表示されていればインストールされています。

```
$ pyenv --version
pyenv 1.2.13
```


## pyenvにPATHを通す
pyenvコマンドを利用するために、pyenvにPATHを通します。PATHを通すとは、コマンド実行ファイルを探しに行くパスを追加することです。

参考）[PATHを通すとは？（Mac OS X）](https://qiita.com/soarflat/items/09be6ab9cd91d366bf71)

下記のコマンドを1つずつ実行してください。

```
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
$ echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
$ source ~/.bash_profile
```

`>> ~/.bash_profile`でスクリプトを`.bash_profile`に追加しています。

また最後に`source`コマンドを使うことで`.bash_profile`に追加した内容を反映できます。


## Pipenvのインストール
Pipenvとは、Pythonのパッケージ管理と仮想環境の構築・切替を自動で行うツールのことです。Pipenvが登場してから、Pythonの開発環境が劇的に快適になりました。この教材でもぜひ導入して活用しましょう。

下記のコマンドでPipenvをインストールします。

```
$ brew install pipenv
```

下記のコマンドでバージョンを確認できます。

```
$ pipenv --version
pipenv, version 2018.11.26
```


## Pythonのインストール
Pipenvには、指定したPythonのバージョンで仮想環境を作成する機能があります。（ただしpyenvがインストールされている必要があります。）

この機能を使って、Pythonをインストールします。

まず先ほどインストールした`pyenv`を使ってインストール可能なPythonnのバージョンを確認します。

以下のコマンドを実行してください。

```
$ pyenv install -l
```

すると下記のようにPythonのインストール可能なバージョンの一覧が表示されます。

```
Available versions:
  2.1.3
  2.2.3
  2.3.7
  ---中略---
  3.7.0
  3.7-dev
  3.7.1
  3.7.2
  3.7.3
  3.7.4
  3.7.5
  3.7.5rc1
  3.8.0
  3.8-dev
  3.9-dev
  .
  .
  .
```

現在の最新のバージョンである3.8.0のバージョンをインストールします。（2019年11月時点）

3.8.0のバージョンが表示されない場合は、`pyenv`を最新にアップグレードする必要があります。アップグレードするには以下のコマンドを実行してください。(**3.8.0が表示されている場合は実行しなくて大丈夫です。**)

```
$ brew upgrade pyenv
```

それでは、以下のコマンドを実行してください。(インストール完了まで数分かかることがあります。)

```
$ pipenv --python 3.8.0
```

インストールが完了したら、PC（サーバー）内で共通に使うためにグローバルで利用するバージョンを設定します。

```
$ pyenv global 3.8.0
```

プロジェクトごとにPythonのバージョンを指定する場合は`global`ではなく`local`を使います。

次にPythonのバージョン情報を確認します。

```
$ python -V
Python 3.8.0
```


## Djangoのインストール
最後にDjangoをインストールします。以下のコマンドを実行してください。(インストール完了まで数分かかることがあります。)

```
$ pipenv install django==2.2.7
```

`==バージョン`を記載することでバージョンを指定してDjangoをインストールできます。今回の場合`2.2.7`のバージョンをインストールしています。

実行ができたら以下のコマンドでDjangoのバージョンを確認します。

```
$ pipenv run python -m django --version
2.2.7
```

これでDjangoのインストールは完了です。

お疲れ様でした。
