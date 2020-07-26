# Dockerを使う準備(Mac編)

このパートでは、MacでDockerを使うための準備をします。

**すでにDocker Desktop for Macを使っているという方はこのパートは読み飛ばして、次のパートに進んでください。**

## Dockerとは

Dockerとは、仮想化技術のひとつです。

Dockerを使うと、パソコンやサーバーに仮想環境を作って、その上でWebサーバーやデータベースなどを動かすことができます。

## Dockerのメリット

Dockerを利用するメリットはさまざまあります。

例えば、Webサーバーやデータベース本体やその設定内容をファイル化できるという点が挙げられます。

そのようなファイルをほかの人に配布することで、誰でも同じ環境を構築できます。

本教材では、そうしたDocker用に作られたファイルを利用して開発環境を作ります。

## Docker Desktop for Macをインストールしよう

MacでDockerを使うために必要なソフトウェアをインストールします。

### 1. Dockerのサイトにアクセスする

[Dockerの公式サイト](https://www.docker.com/)にアクセスし、右上の`Get Started`を選択してください。

![top](https://user-images.githubusercontent.com/42920380/88484358-ff208c80-cfa8-11ea-84cd-8ef982727c96.png)

### 2. Docker Desktop for Macをダウンロードする 

Docker Desktopの`Download for Mac`を選択してください。

![download](https://user-images.githubusercontent.com/45457022/81477576-77ea3500-9253-11ea-9191-ed46bb732ea5.png)

`Docker.dmg`のダウンロードが開始されます。

### 3. アプリケーションフォルダへの移動

`Docker.dmg`のダウンロードが完了したら、これを実行してください。

以下の画面が表示されるので、左のDockerのアイコンを右のアプリケーションフォルダにドラッグします。

<img width="832" alt="move" src="https://user-images.githubusercontent.com/45457022/81477693-f3e47d00-9253-11ea-8300-2c72aed9aef2.png">

### 4. アプリケーションフォルダのDockerアイコンを選択して起動する

アプリケーションフォルダのDockerアイコンを選択して起動してください。

以降、Docker Desktopは起動しっぱなしで問題ありません。

Docker Desktopが起動中であるかどうかは、Macの右上の黒いDockerアイコン表示でわかります。

<img width="26" src="https://user-images.githubusercontent.com/45457022/61193993-b7aac380-a6f9-11e9-9b2b-ba019e310d59.png">

以上で、Dockerを使う準備は完了です。
