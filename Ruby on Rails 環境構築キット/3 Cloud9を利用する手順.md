> ここではCloud9の環境構築方法を記載しています。
>
> ここから教材

# Cloud9を利用する手順
今回のパートではCloud9を利用する手順を記載しています。Windowsの方は本パートを参考にCloud9を利用できるようにしてください。

**※）お使いのPCがMacの方はこちらのパートは読み飛ばされて大丈夫です。**


## Cloud9とは
Cloud9はアプリケーション開発やデータベースなどをクラウド環境で利用できるサービスです。Cloud9を使えば、簡単にプログラミング開発環境を構築できます。


## AWSアカウントを取得
Cloud9を使うためにはAWSアカウントが必要になります。AWSとはAmazon Web Servicesの略でクラウドコンピューティングサービスを提供しています。

AWSアカウントを既にお持ちの場合は、[AWS](https://aws.amazon.com/jp/)にログインしてください。

AWSのアカウントを持っていない場合は、下記のリンクからAWSアカウントを作成してください。

- [AWSアカウントの作成](https://portal.aws.amazon.com/billing/signup#/start)

AWSアカウント作成の流れに関しては公式のリンクが非常に分かりやすいのでこちらを参考にしてください。

- [AWS アカウント作成の流れ](https://aws.amazon.com/jp/register-flow/)


## AWSにログイン
AWSアカウントを作成したら、AWSにログインしてください。

ログインは下記のリンクからログインできます。

[AWSコンソール](https://console.aws.amazon.com/)

ログインができたら下記のような画面に遷移します。

![image](https://i.gyazo.com/e0aff5a873b079a38e714a99f54e4b3b.png)

画面中央付近にある検索ボックスから「Cloud9」と入力すると、Cloud9の開発環境を作成するためのページに遷移します。

![image](https://i.gyazo.com/75b03abc66a1b110ee04fe853479efd9.jpg)


## Cloud9の開発環境を作成
ではCloud9の開発環境を作成していきます。下記の画面にある「Create environment」をクリックしてください。

![image](https://i.gyazo.com/6e239e5a81cf85436a04e7c5d6956f07.jpg)

次に`Name`のフォームの箇所にアプリ名を入力します。アプリ名を入力したら、「Next step」をクリックしてください。

![image](https://i.gyazo.com/651fe2f4578596065cdc3a9bbb6eda85.png)

次に下記の画像のような画面に遷移します。この画面ではそのまま「Next step」を入力してください。

![image](https://i.gyazo.com/bcb279e686aa08736a57cb554d7e448d.png)

次に下記の画像のような画面に遷移します。この画面ではそのまま「Create environment」を入力してください。

![image](https://i.gyazo.com/629ca88db02a7aeb6ea7b56e53a91937.png)

すると下記の画像のように表示されていればCloud9の環境構築ができています。（下記の画面が表示されるまでに1~2分かかることがあります。）

![image](https://i.gyazo.com/891650d70f389033798c010402fbfaff.png)


## Cloud9のインデントを設定
Rubyの世界では、インデントに2つのスペースを使うのが常識になっているので、Cloud9のエディタのインデントも2つに設定するのをおすすめします。

インデントの設定を変更するには、右上の歯車アイコンをクリックし、「Soft Tabs」の箇所を4から2に変更します。

![image](https://i.gyazo.com/48ead0c37c0d83acd8348e1bd075218c.png)


## Cloud9のテーマを設定
現状でも開発を進めることはできますが、Cloud9の見た目をかっこよくしたい方は読み進めてください。

**※）必ずしもテーマを設定する必要はありません。テーマを設定したい人だけ設定してください。**

テーマはヘッダーにある「View」の「Themes」で設定できます。例えば、下記の動画のように「Classic Dark」を選択すると、ダークなデザインになります。

![image](https://i.gyazo.com/549bd7d8a81071824161c226a10c3da8.gif)

以上で今回のパートは終了です。

お疲れさまでした。
