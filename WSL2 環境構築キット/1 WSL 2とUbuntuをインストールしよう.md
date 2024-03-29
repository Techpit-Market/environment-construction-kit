>ここではWindowsでの開発環境構築のためのWSL 2とUbuntuのインストール手順を記載しています。
>
>教材を作成するに当たって必要であれば説明を付け加えてください。
>
>ここから教材
# WSL 2とUbuntuをインストールしよう
このパートではWindows10上で開発環境を構築するために必要な **WSL** と **Ubuntu** というシステムをインストールします。

## WSLとは
WSL(Windows Subsystem for Linux)とはLinux環境をWindows10上で直接実行できるようにするためのシステムです。

今回は2021年10月現在で最新のバージョンであるWSL 2をインストールします。

## Ubuntuとは
今回学習を進めるにあたって、開発環境の構築をOSのひとつである**Linux**上で行ないます。

Linuxを使用するには、基本的に**Linuxディストリビューション**を使用します。

ディストリビューション（Distribution）は「流通」や「配布」という意味で、Linuxのアプリケーションやライブラリをひとまとめにして、PCにインストールすればすぐに使える状態にした配布物を指します。

Linuxディストリビューションはいくつか種類がありますが、今回は無償で使用できる、代表的なLinuxディストリビューションのひとつである**Ubuntu**をインストールします。

## PowerShellの起動
コマンドでWindowsの操作をするためのツールにコマンドプロンプトというものがありますが、WSL 2のインストールではコマンドプロンプトよりも高機能な**PowerShell**というツールを使用します。

PowerShellは最新のWindows10では最初からインストールされています。

それではPowerShellを起動してみましょう。

画面左下の「Windowsロゴ」を**右**クリックしてください。

<img src="https://user-images.githubusercontent.com/25563739/128489901-d56b92bd-4c0d-4863-907b-173326c0ad56.png" width="800">

以下のようにメニューが表示されるので、「Windows PowerShell（管理者）」をクリックしてください。

<img src="https://user-images.githubusercontent.com/25563739/128489905-b96620fd-3b20-45aa-9726-c8a63e43740a.png" width="300">

管理者特権のアクセス許可を求めるメッセージが表示されるので、「はい」をクリックしてください。

以下のようなウインドウが表示されれば成功です。

<img src="https://user-images.githubusercontent.com/25563739/128489906-3ceb494f-b8c1-4a2e-b325-e2456c4e7313.png" width="700">

## WSL 2とUbuntuのインストール
PowerShellを開いたら、WSL 2とUbuntuをインストールします。

以下のコマンドを実行してください。

```console
wsl --install
```

上記のコマンドを実行すると、WSL 2とUbuntuが同時にインストールされます。

以下のようなメッセージが表示されればインストール成功です。

<img src="https://user-images.githubusercontent.com/25563739/137863076-a8e8d854-4e11-45a8-986b-1ead3ad0c787.png" width="850">

WSL 2を有効にするには再起動する必要があるので、電源オプションから再起動してください。

<img src="https://user-images.githubusercontent.com/25563739/137863400-fd3666a1-6e62-40d0-aac0-d5ee107063b3.png" width="600">

再起動すると、以下のようなUbuntuのコンソールウインドウが自動で開き、数分待つように求められます。

<img src="https://user-images.githubusercontent.com/25563739/128489946-dab5adb7-3737-4c6e-b01b-8dd141275ab1.png" width="800">

## Ubuntuのユーザーアカウントの作成

数分後、以下のようなメッセージが表示されたら、任意のユーザー名を入力してください。

<img src="https://user-images.githubusercontent.com/25563739/128489947-fcc6cf99-1934-48f7-88a9-87942ffb7c33.png" width="800">

続いて任意のパスワードを入力してください。

<img src="https://user-images.githubusercontent.com/25563739/128492495-6a40e926-06b2-49d9-b980-1bbb14c8bde2.png" width="800">

再度パスワードを求められるので、再入力してください。

<img src="https://user-images.githubusercontent.com/25563739/128489952-cd62495f-6f38-4881-ab08-671ec0b3426b.png" width="800">

以下のような表示になれば、Ubuntuを使用する準備は完了です。

<img src="https://user-images.githubusercontent.com/25563739/128492998-153b0846-267c-4567-8d49-d63173847661.png" width="800">

以上でWSL 2とUbuntuのインストールは完了です。

お疲れさまでした。
