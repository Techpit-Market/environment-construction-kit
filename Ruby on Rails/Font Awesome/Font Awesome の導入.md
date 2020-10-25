> 動作確認やファイルパスは教材に合わせて修正してください


# Font Awesome の導入
今回のパートではFont Awesomeを導入していきます。

Font Awesomeを導入することで、Web上でよく利用されるアイコンをアイコンフォントという文字として使うことができます。


## 本パートのゴール
本パートでは、下記の画像のようにヘッダーのリスト作成のところにアイコンを表示させます。

![image](https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/15288/098fbb02-7134-486b-9328-7cc62c3727f9.png)


## ゴールまでの流れ
1. Font Awesome の導入
2. Font Awesome が導入されたか確認

では、実際に進めてみましょう。


## 1. Font Awesome の導入
それでは、Font Awesome を導入していきます。Bootstrapと同様yarnを使って導入します。以下のコマンドを実行してください。

```console
yarn add @fortawesome/fontawesome-free
```

コマンドを実行すると、次のような結果が表示されます。

```console
yarn add @fortawesome/fontawesome-free
yarn add v1.16.0
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning " > webpack-dev-server@3.11.0" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
warning "webpack-dev-server > webpack-dev-middleware@3.7.2" has unmet peer dependency "webpack@^4.0.0".
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 1 new dependency.
info Direct dependencies
└─ @fortawesome/fontawesome-free@5.15.1
info All dependencies
└─ @fortawesome/fontawesome-free@5.15.1
✨  Done in 5.19s.
```

`package.json` ファイルには以下のコードが追加されます。

```diff:pacakge.json
{
  "name": "kanban",
  "private": true,
  "dependencies": {
+   "@fortawesome/fontawesome-free": "^5.15.1",
    "@rails/actioncable": "^6.0.0",
    "@rails/activestorage": "^6.0.0",
    "@rails/ujs": "^6.0.0",
```

次に、`app/javascript/stylesheets/application.scss`にFont Awesome のCSSを読み込みます。

```diff:app/javascript/stylesheets/application.scss
@import '~bootstrap/scss/bootstrap';

@import "custom";
+ @import '~@fortawesome/fontawesome-free/scss/fontawesome';
```

次にyarnでインストールした Font Awesome のパッケージを利用できるように`import`します。

`app/javascript/packs/application.js` に以下のコードを追加してください。

```diff:app/javascript/packs/application.js
import 'bootstrap';
import '../stylesheets/application';
+ import '@fortawesome/fontawesome-free/js/all';
.
// 中略
```

以上でFont Awesomeの導入は終了です。


## 2. Font Awesome が導入されたか確認
実際にFont Awesomeが機能するか確認します。

http://localhost:3000 にアクセスしてください。ヘッダーのリスト作成のところにアイコンが表示されていれば、うまく動作しています。

![image](https://i.gyazo.com/267fe8da1a5868b6b4a9f0ffa177f72e.png)

Font Awesome を導入することで、cssでアイコンを表示できました。

今回のアイコンに該当するコードは下記になります。

```erb:app/views/layouts/application.html.erb
<i class="fas fa-edit"></i>
```

`fa-edit`はアイコン名になります。このアイコン名は[Font Awesome の公式サイト](https://fontawesome.com/icons?d=gallery)から調べられます。

今回は「edit」のアイコンを利用しています。

[Font Awesome - edit](https://fontawesome.com/icons/edit?style=solid)

以上で今回のパートは終了です。

お疲れ様でした。
