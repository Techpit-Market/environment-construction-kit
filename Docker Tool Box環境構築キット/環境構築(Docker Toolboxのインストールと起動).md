# 環境構築(Windows10 Home)
Windows10 Homeを使っている方向けの環境構築方法です。

このパートではdockerをインストールした後に、起動確認までを行います。

## Windows10 HomeでDocker Toolboxをインストールする
本教材で作るWebアプリケーションではDockerを使って、環境を作成して開発を行っていきます。

公式サイトのこちらから、Docker Toolboxをダウンロードします。

[docker.com](https://github.com/docker/toolbox/releases)

![image](https://gyazo.com/19b7bd18e13b64bad0658e9e6f896d30.png)

教材執筆時点の最新バージョンが「v19.03.1」でしたので、「v19.03.1」をインストールします。

「**DockerToolbox-19.03.1.exe**」をクリックして任意のフォルダにインストールしましょう。

インストールが完了したら起動します。

以下のような画面が表示されたら「**Next**」をクリックしてください。

![image](https://gyazo.com/aa88559019dc2f710c1ce746f5cade67.png)

インストールするフォルダを選択します。ここでは特に変更せずデフォルトのまま進めます。「**Next**」
を選択してください。
![image](https://gyazo.com/c5c3e2c15eeafc2782ca885e6594a5ac.png)

「Git」をインストールしたことがない方は、「**Git for Windows**」にチェックをいれましょう。それ以外はデフォルトの設定で進めます。

![image](https://gyazo.com/4a90d106273b7953b0400009093f91df.png)

以下の画面では、全てつにチェックを入れて「**Next**」を選択します。

![image](https://gyazo.com/062e4c6834ec03807f01bca16ec4d2df)

基本的な設定は以上です。「**install**」をクリックしましょう。

![image](https://gyazo.com/099fe9c9c7aaefc8b8b36fe998020384.png)

 デスクトップに「**Kitematic**」が作成されているので、ダブルクリックして起動しましょう。
 
Kitematicを初回起動した場合、Docker仮想マシンが作成されます。

100%になるまで少し待ちましょう。

 ![image](https://gyazo.com/be491576b5b1b79e939ba5dc153e738a)

 デスクトップに「**Docker Quickstart Terminal**」が作成されているので、ダブルクリックして起動しましょう。
 
 初回の起動には少々時間がかかります。
 
 以下のような画面が表示されれればDocker Toolboxのインストールは完了です。
 
 ```
                        ##         .
                  ## ## ##        ==
               ## ## ## ## ##    ===
           /"""""""""""""""""\___/ ===
      ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
           \______ o           __/
             \    \         __/
              \____\_______/

docker is configured to use the default machine with IP 192.168.99.100
For help getting started, check out the docs at https://docs.docker.com


Start interactive shell
 ```

## dockerコマンドとdocker-composeコマンドの確認

起動が完了したら、`docker`コマンドと`docker-compose`コマンドが使えるか確認します。

Docker Quickstart Terminalを開いて、次のコマンドを実行してください。

```
$ docker -v
```

以下のようにdockerのバージョンが表示されます。

```
$ docker -v
Docker version 19.03.1, build 74b1e89e8a
```

docker-composeコマンドも確認してみましょう、次のコマンドを実行してください。

```
$ docker-compose -v
```

docker-composeのバージョンが表示されました。

```
$ docker-compose -v
docker-compose version 1.24.1, build 4667896b
```

ここまでで、dockerのインストールと起動確認は完了です。

## Docker Toolbox使用時の注意点
教材内でローカルサーバーからアプリケーションにアクセスする際、「http://localhost:8080/ にアクセスします。」という記載がありますが、Docker Toolboxでは`localhost`でローカルサーバーにアクセスできません。

直接IPを指定する必要があります。

IPアドレスを確認するには、Docker Quickstart Terminalで以下のコマンドを実行してください。

```
$ docker-machine ls
```

実行結果のURLの部分にIPアドレスが表示されます。ここでは、`192.168.99.100`が仮想マシンのIPアドレスです。
```
$ docker-machine ls
NAME      ACTIVE   DRIVER       STATE     URL                         SWARM   DOCKER      ERRORS
default   *        virtualbox   Running   tcp://192.168.99.100:2376           v19.03.12
```


## トラブルシューティング

Docker Quickstart Terminalを初回に起動した際に、以下のような画面が表示されることがあります。

```
(default) This is a known VirtualBox bug. Let's try to recover anyway...
Error creating machine: Error in driver during machine creation: Error setting up host only network on machine start: The host-only adapter we just created is not visible. This is a well known VirtualBox bug. You might want to uninstall it and reinstall at least version 5.0.12 that is is supposed to fix this issue
Looks like something went wrong in step ´Checking if machine default exists´... Press any key to continue...
```

このエラーはVirtualBoxのバージョンによるエラーですので、一度VirtualBoxをアンインストールし、以下のURLから、再度VirtualBoxだけインストールしなおしましょう。

https://www.virtualbox.org/wiki/Downloads
