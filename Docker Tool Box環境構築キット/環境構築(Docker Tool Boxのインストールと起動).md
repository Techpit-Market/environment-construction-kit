# 環境構築(Windows)
Windows10 Homeを使っている方向けの環境構築方法です。

このパートではdockerをインストールした後に、起動確認までを行います。

## Windows10 HomeでDocker Tool Boxをインストールする
本教材で作るWebアプリケーションではdockerを使って、環境を作成して開発を行っていきます。

まずはDocker Tool Boxをインストールして、`docker`コマンドと`docker-compose`コマンドを使えるようにしましょう。

公式サイトのこちらから、ダウンロードします。

[docker.com](https://github.com/docker/toolbox/releases)

![image](https://i.gyazo.com/7765dc96feda3746c2090023789856f9.png)

ダウンロードしたファイルを開いてください。

下記のようにチェックされていることを確認して、OKボタンをクリックします。

![image](https://i.gyazo.com/011543ce9c7978b6c28649ff25487d52.png)

インストールが始まるので、待ちます。

完了すると、このようにメッセージが表示されるので、OKボタンをクリックして閉じます。

![image](https://i.gyazo.com/11766e64059cbfb61ab814689586a7d6.png)

Desktopにショートカットが作成されているので、クリックして起動します。

![image](https://i.gyazo.com/5994f6e2590c6a5ca955896cf5c10a10.png)

パッと見た感じでは起動しているか確認できませんが、常駐しているアプリケーションを確認するとDockerのアイコンが表示されています。

![image](https://i.gyazo.com/cd52a1c6d48128061741432ddbad6b25.png)

ここまでで、Docker Desktop for Windowsの起動完了です。

## dockerコマンドとdocker-composeコマンドの確認

起動が完了したら、`docker`コマンドと`docker-compose`コマンドが使えるか確認します。

コマンドプロンプトを開いて、次のコマンドを実行してください。

※起動方法やコマンド実行方法は *「0-8 ターミナル・コマンドプロンプト起動方法」* を確認してください。

```
$ docker -v
```

dockerのバージョンが表示されました。

```
$ docker -v
Docker version 19.03.12, build 48a66213fe
```

docker-composeコマンドも確認してみましょう、次のコマンドを実行してください。

```
$ docker-compose -v
```

docker-composeのバージョンが表示されました。

```
$ docker-compose -v
docker-compose version 1.27.2, build 18f557f9
```

ここまでで、dockerのインストールと起動確認は完了です。
