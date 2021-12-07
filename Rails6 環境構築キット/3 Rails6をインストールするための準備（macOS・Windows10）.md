> ここでは、Node.jsとyarnのインストール方法を記載しています。
> 
> Rubyの環境構築キットでasdfを用いてRubyをインストールしていることを前提としています。
>
> Windows10はWSL2を用いてUbuntu環境を構築していることを前提としています。
>
> ここから教材

# Rails6をインストールするための準備（macOS・Window10）
このパートではRailsの環境構築に必要なNode.jsとyarnをインストールします。

Rails6では、Rails上でJavaScript開発をするための**Webpacker**というツールが標準で実装されています。

今回インストールするNode.jsとyarnはWebpackerをインストールするために必要なツールになります。

## Node.jsの確認
すでにNode.jsがインストールされているかどうかはコマンドで確認できます。

ターミナルを開いて以下のコマンドを入力してみましょう。

```console
node -v
```

以下のようにインストールされているNode.jsのバージョンが表示されれば、すでにインストール済みです。

```
v16.13.1
```

Node.jsの最新バージョンを確認するには以下の公式ページを参照してください。

- [Node.js](https://nodejs.org/ja/)

最新バージョンは以下の画像の赤枠で囲った箇所に記載されています(以下の画像は2021年12月現在のもの)。

<img width="1040" src="https://user-images.githubusercontent.com/25563739/144869715-cc2188fb-fff7-4c9e-9c93-d697a2251eae.png">

もし`v13.○.○`や`v14.○.○`など、古いバージョンを使用している場合は、必ず最新バージョンにアップデートしてください。

`v16.○.○`を使用している方も、最新バージョンでない場合はアップデートすることをおすすめします。

## yarnの確認
すでにyarnがインストールされているかどうかはコマンドで確認できます。

ターミナルを開いて以下のコマンドを入力してみましょう。

```console
yarn -v
```

以下のようにインストールされているNode.jsのバージョンが表示されれば、すでにインストール済みです。

```
yarn 1.22.17
```

yarnの最新バージョンを確認するにはyarnのGithubリポジトリを参照してください。

- [Releases · yarnpkg/yarn | Github](https://github.com/yarnpkg/yarn/releases)

最新バージョンは以下の箇所に記載されています(以下の画像は2021年12月現在のもの)。

<img width="1040" src="https://user-images.githubusercontent.com/25563739/145044192-ecc1366a-8b34-414c-b45b-9eb3b98bb294.png">


最新バージョンでない場合はアップデートすることをおすすめします。

## Node.jsのインストール
最初に**Node.js**をインストールします。

Node.jsはJavaScriptの実行環境です。

通常、ブラウザ上で実行されるJavaScriptをOS上で実行するために必要になります。

Rubyと同様にasdfで管理することができます。

それでは、asdfを用いてNode.jsのインストールを行ないましょう。

## 必要なパッケージのインストール
Node.jsのインストールに必要なパッケージをHomebrewを利用してインストールします。

以下のコマンドを実行してください。

```console
brew install gpg gawk
```

インストールできたか確認します。

まず、以下のコマンドを実行して、gpgがインストールできたら確認してください。

```console
gpg --version
```

以下のようなメッセージが表示されればインストール成功です。

```
gpg (GnuPG) 2.3.1
・
・
・
```

続いてgawkの確認をします。

以下のコマンドを実行してください。

```console
gawk --version
```

以下のようなメッセージが表示されればインストール成功です。

```
GNU Awk 5.1.0, API: 3.0 (GNU MPFR 4.1.0, GNU MP 6.2.1)
・
・
・
```

### プラグインのインストール
続いて、Node.jsをインストールするのに必要なプラグインをインストールします。

以下のコマンドを実行してください。

```console
asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
```

以下のコマンドを実行して、プラグインがインストールできたか確認しましょう。

```console
asdf plugin list
```

以下のように表示されれば成功です。

```
nodejs
```

### Node.jsのインストール
今回はLTS（Long Term Support）と呼ばれる、長期サポートが保証されている最新のバージョンをインストールします。

以下のコマンドを実行してください。

```console
asdf install nodejs lts
```

インストールが完了すると、以下のようなメッセージが表示されます。

```
・
・
・
node-v16.13.0-darwin-x64.tar.gz: OK
Linking "lts" to "16.13.0"
```

Node.jsがインストールされたか確認しましょう。

下記のコマンドを入力してください。

```console
asdf list nodejs
```

以下のように`lts`と表示されれば成功です。

```
  16.13.0
  lts
```

## バージョンを設定する
先ほどインストールしたLTSバージョンを使用する設定をします。

バージョンの設定は、OS全体(グローバル)で同じバージョンを設定する方法と、プロジェクトごと(ローカル)に異なるバージョンを設定する方法があります。

ここではグローバルに設定する方法を説明します。

以下のコマンドを実行してください。

```console
asdf global nodejs lts
```

コマンドを実行しても特にメッセージは表示されません。

バージョンが設定されたか確認しましょう。

以下のコマンドを実行してください。

```console
node -v
```

以下のようにバージョンが表示されれば成功です。

```
v16.13.0
```

以上でNode.jsの環境構築は完了です。

## yarnのインストール
次に**yarn**をインストールします。

yarnはJavaScriptのライブラリの利用に必要なパッケージマネージャです。

yarnもNode.jsと同様にasdfで管理することができます。

それでは、asdfを用いてyarnのインストールを行ないましょう。

### プラグインのインストール
まずはyarnを管理するためのプラグインをインストールします。

以下のコマンドを実行してください。

```console
asdf plugin-add yarn
```

コマンドを実行すると以下のようなメッセージが表示されます。

```
updating plugin repository...remote: Enumerating objects: 21, done.
remote: Counting objects: 100% (21/21), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 18 (delta 11), reused 9 (delta 5), pack-reused 0
Unpacking objects: 100% (18/18), 3.05 KiB | 66.00 KiB/s, done.
From https://github.com/asdf-vm/asdf-plugins
   232d2df..d51b43b  master     -> origin/master
HEAD is now at d51b43b feat: deck plugin (#509)
```

以下のコマンドを実行して、プラグインがインストールできたか確かめましょう。

```console
asdf plugin list
```

以下のように、yarn と表示されていれば成功です。

```
ruby
yarn
```

### yarnのインストール
次に最新のyarnをインストールします。

以下のコマンドを実行してください。

```console
asdf install yarn latest
```

コマンドを実行すると以下のようにメッセージが数十行表示されます。

```
・
・
・
gpg: keybox'~/.asdf/keyrings/yarn/pubring.kbx'が作成されました
gpg: ~/.asdf/keyrings/yarn/trustdb.gpg: 信用データベースができました
gpg: 鍵1646B01B86E50310: 公開鍵"Yarn Packaging <yarn@dan.cx>"をインポートしました
・
・
・
```

yarnがインストールできたか確かめましょう。

以下のコマンドを実行してください。

```console
asdf list yarn
```

以下のようなメッセージが表示されれば、インストール成功です。

```
 1.22.17
```

### バージョンを設定
インストールが完了したら、バージョンを使用する設定をしましょう。

以下のコマンドを実行してください。

```console
asdf global yarn latest
```

コマンドを実行しても特にメッセージは表示されません。

最後にyarnコマンドが使用できるか確認しましょう。

以下のコマンドを実行してください。

```console
yarn -v
```

以下のように、バージョン数が表示されれば成功です。

```
1.22.17
```

以上でこのパートは終了です。

お疲れさまでした。
