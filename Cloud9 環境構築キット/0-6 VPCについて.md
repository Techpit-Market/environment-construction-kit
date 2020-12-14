# VPCの作成

AWS Cloud9を使用するには**VPC**を作成する必要があります。

AWS公式サイトに記載されているVPCに関する説明は以下の通りです。

[Amazon Virtual Private Cloud](https://aws.amazon.com/jp/vpc/)

>Amazon Virtual Private Cloud (Amazon VPC) では、AWS クラウドの論理的に分離されたセクションをプロビジョニングし、お客様が定義した仮想ネットワーク内の AWS リソースを起動することができます。自分の IP アドレス範囲の選択、サブネットの作成、ルートテーブルやネットワークゲートウェイの設定など、仮想ネットワーキング環境を完全に制御できます。

簡単に言うと、AWSが持っている共有クラウドの中に、各ユーザーの空間を割り当てるような仕組みです。

ここでは詳細な説明は省き、Cloud9用のVPCの設定方法のみ説明していきます。


「Cloud9の環境構築」でデフォルトのVPCが設定されていた方は設定不要ですので読み飛ばしてください。

::: info
VPCはアカウント作成時に自動で作成してくれます。

このパートは何らかの事情でVPCを削除してしまった方向けです。
:::

### VPCの作成手順

以下のURLからコンソールにログインしましょう。

https://us-east-2.console.aws.amazon.com/console/

「**サービスを検索する**」の欄にVPCと入力してクリックしてください。

![serch_VPC](https://i.gyazo.com/4a7b7d209f06037c8958c5935e55b26f.png)

以下のような画面が表示されるので、「**VPCウィザードの起動**」をクリックしてください。

![VPC_wizard](https://i.gyazo.com/6f818dbd64c00d891e67c74227f20acb.png)

次に、「1 個のパブリックサブネットを持つ VPC」をクリックし、「**選択**」をクリックします。

![VPC_choice](https://i.gyazo.com/316393bdc7931058802e9cce61b62b2b.png)

以下のような画面が表示されます。

![VPC_IP](https://i.gyazo.com/ff0a8910821886f7d0bfd09d9789c732.png)

特に設定は変更せずに「**VPCの作成**」をクリックしてください。


以下のような画面が表示されていれば、正常にVPCが作成されています。

![VPC_OK](https://i.gyazo.com/aafc733bcfe926b01834f1677dec7c8a.png)

右下の「**ok**」ボタンをクリックしてください。

以上でVPCの作成は完了です。