---
title: "Docker Desktop のインストール(Windows)"
emoji: "🐳"
type: "template"
---


# Docker Desktopのインストール（Windows）
このパートでは、Dockerを使うことができるように、Docker Desktopのインストールをします。

もし既にお手元のPCにDocker Desktopがインストール済みであれば、このパートは読み飛ばしても大丈夫です。

また、お使いのWindowsの種類によって操作が異なります。該当の見出しまで進んでください、

| 種類 | 環境構築手順 |
|:---|:---|
|Windows 10 Pro|Docker Desktop for Windowsをダウンロード|
|Windows 10 Enterprise |Docker Desktop for Windowsをダウンロード |
|Windows 10 Home バージョン2004,ビルド19041以上|Docker Desktop for Windowsをダウンロード|
|上記以外|WSL 2のインストール→Docker Desktop for Windowsをダウンロード|

## WSL 2のインストール

**WSL 2**のインストールにはWindowsをバージョン2004,ビルド19041以上にアップデートする必要があります。

以下のURLからアップデートしましょう。

「Windows 10 October 2020 Update」以降のアップデートであれば問題ありません。※インストールには数時間かかる場合がございます。

ここからはWSL 2のインストールを行っていきます。

1. `コマンドプロンプト`もしくは`PowerShell`を管理者権限で起動します

2. Linux 用 Windows サブシステムを有効にする

```shell
$ dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

以下のように表示されれば正常に実行されています。

```shell
$ dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
バージョン: 10.0.19041.572

イメージのバージョン: 10.0.19042.630

機能を有効にしています
[==========================100.0%==========================]
操作は正常に完了しました。
```

3. 仮想マシンの機能を有効にする

```shell
$ dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

```shell
$ dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

展開イメージのサービスと管理ツール
バージョン: 10.0.19041.572

イメージのバージョン: 10.0.19042.630

機能を有効にしています
[==========================100.0%==========================]
操作は正常に完了しました。
```

ここまでの設定が完了したら一度ＰＣを再起動しましょう。

4. Linux カーネル更新プログラム パッケージをダウンロードする
https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi

ダウロードが完了したら、ダブルクリックで起動します。

以下のような画面が表示されるので、「**Next**」をクリックしましょう。

![image](https://i.gyazo.com/736f28d6f796ef11eed4b60901f22902.png)

管理者特権のアクセス許可を求めるメッセージが表示されたら。[はい] を選択してください。

5. WSL 2 を既定のバージョンとして設定する
 `コマンドプロンプト`もしくは`PowerShell`を管理者権限で起動します。

 以下のコマンドでWSL 2 を既定のバージョンとして設定します。
 ```shell
$ wsl --set-default-version 2
 ```

以下のような文章が表示されます。
  ```shell
$ wsl --set-default-version 2
WSL 2 との主な違いについては、https://aka.ms/wsl2 を参照してください
 ```

6. Linux ディストリビューションをインストール

[Microsoft Store](https://aka.ms/wslstore)を開きます。

右上の検索窓に「Ubuntu」と入力します。

ここでは教材執筆時点で最新版の「Ubuntu 20.04 LTS」をインストールしていきます。

※インストールには数分かかる場合があります。

![image](https://i.gyazo.com/92176d7516f0cc404f0fda85a3deb46f.png)

インストールが完了すると、「**起動**」ボタンが表示されるのでクリックしてください。

![image](https://i.gyazo.com/e2b963279806bf4080b3c9296989a85e.png)

Ubuntuのターミナルが立ち上がり、

- ユーザーネーム
- パスワード

を設定します。このパスワードは忘れないようにしましょう。

```ubuntu
Installing, this may take a few minutes...
Please create a default UNIX user account. The username does not need to match your Windows username.
For more information visit: https://aka.ms/wslusers
Enter new UNIX username: <任意のユーザーネーム>
New password:<任意のパスワード>
Retype new password:<パスワード再入力>
```

 `コマンドプロンプト`もしくは`PowerShell`で以下のコマンドを実行し、`Ubuntu`が起動していることを確認してください。

```shell
$ wsl --list --verbose
  NAME            STATE           VERSION
* Ubuntu-20.04    Running         2
```

WSL 2のインストールは以上になります。「Docker Desktop for Windowsのダウンロード」に進みましょう。

## Docker Desktop for Windowsのダウンロード
[Docker公式サイト](https://www.docker.com/products/docker-desktop)にアクセスしてください。

「Download for Windows(stable)」を選択します。

![image](https://gyazo.com/2b5cc7d3a239c267e9c3b19b327d0d7d)

インストールが完了したら、ダブルクリックで起動します。

以下のチェックボックスにはどちらもチェックを入れて「ok」をクリックします。

![image](https://i.gyazo.com/c6f432b505c15ce058fef20907b79bb6.png)

するとDockerのインストールが始まります。少々時間がかかる場合があります。

![image](https://i.gyazo.com/3fe7857457d49bbc92db9262db6e7a7a.png)

以下のような画面が表示されればインストールは完了です。「Close and log out」をクリックして、「Docker Desktop for Windowsを起動」に進みましょう。

![image](https://i.gyazo.com/fbde4e91696293325e0bd1310c2d25ea.png)

## Docker Desktop for Windowsを起動

デスクトップに作成されている「Docker Desktop」をダブルクリックして起動します。

「Start」をクリックします。

![image](https://i.gyazo.com/ffd4008f74ec58cacded3faa1f911b7f.png)

画面右側にコマンドを入力して、バージョンの確認を行います。

![image](https://i.gyazo.com/b57ddde79bb32c6fe5d1208d7c065ad5.png)

```shell
$ docker -v
$ docker-compose -v 
```

それぞれ以下のように表示されればDockerは正常に起動されています。

```shell
$ docker -v
Docker version 19.03.13, build 4484c46d9d
$ docker-compose -v 
docker-compose version 1.27.4, build 40524192
```

以上でDocker Desktop for Windowsの環境構築は終了です。
