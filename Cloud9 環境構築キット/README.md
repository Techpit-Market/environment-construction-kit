# Cloud9環境構築キット

このフォルダはCloud9環境構築キットです。

AWSアカウントの作成からCloud9の起動、簡単な基本操作を解説しています。

執筆中のリポジトリにコピーして使用してください。
必要があれば教材に合わせて修正して使用してください。

Cloud9でサポートしている言語は以下のサイトをご参考にしてください。

[AWS公式ユーザーガイド](https://docs.aws.amazon.com/cloud9/latest/user-guide/language-support.html)

## 【注意点】バージョンについて

Cloud9にデフォルトでインストールされているバージョンは古い可能性があります。
Ruby(Ruby on Rails)、PHP(Laravel)のバージョンの確認手順については0-3に記載しておりますので、ご活用ください。
※バージョンを指定する部分はリライトして使ってください。

【2020年11月現在】
- Ruby: 2.6.3
- Ruby on Rails: 5.0.0
- PHP: 5.6.40 
- Laravel: 未インストール
- Node.js: 10.23.0
- Python: 3.6.12

## DBについて
SQLite3がAmazon Linuxだと使えない場合があります。
インストールするかCloud9を立ち上げる際に、`Ubuntu`を選択するようにしてください。
※Rails6はUbuntuを選択するように0-2の記載を変更してください。
