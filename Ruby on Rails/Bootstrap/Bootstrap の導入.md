> 動作確認の箇所は、作成されている教材に合わせて修正してください


# Bootstrap の導入
今回のパートではBootstrapを導入していきます。

Bootstrapは有名なWebフレームワークで、CSSを細かく指定せずにサイトをある程度形にできます。レスポンシブにも対応してくれる便利なツールです。Bootstrapを導入するとWebアプリケーションを効率よく開発できます。


## 本パートのゴール
今回の目標は、Bootstrapを導入して下記の画像のように青色のボタンを表示するところまで実装していきます。

![image](https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:2500/https://www.filepicker.io/api/file/j2Ntm0ovQcK99BjoDgh1)


## ゴールまでの流れ
1. Webpackerとは
2. BootstrapをWebpackerで導入
3. Bootstrapが導入されたか確認

それでは、実際にjQueryとBootstrapの導入を行いましょう。


## 1. Webpackerとは
今回Bootstrapを導入するにあたって、Webpackerを使って導入していきます。

Webpackerとは、複数のJavaScriptファイルなどを1つにまとめて出力するツールであるwebpackを簡単にRailsアプリケーションに統合できるGemです。

Rails5.1から標準でサポートされるようになりました。

webpackとはモジュールバンドラツールのことで、昨今のモダンなJavaScript開発で必須となりつつある仕組みです。

以下の画像はwebpackの公式サイトのイメージ図になります。

![image](https://i.gyazo.com/5dd6b69fd05b33f454840f7f2f13993a.png)

参考）[webpack](https://webpack.js.org/)

※ 本教材では、webpackについては詳しく解説していません。詳しく解説しようとすると、webpackだけで1つの教材ができるくらいボリュームがあるためです。そのため詳しく学びたい方はご自身で調べていただければと思います


## 2. BootstrapをWebpackerで導入
Webpakcerをインストールするには、まず`Gemfile`に以下のコードを追加します。ただ先ほど説明した通り、Rails5.1以降標準でサポートされているため、デフォルトでGemが追加されています。

一応Gemfileを確認してみましょう。

```
kanban
└── Gemfile
```

```Gemfile
gem 'webpacker', '~> 4.0'
```

なのでGemは追加する必要はありません。

Gemfileにwebpackerというgemがあることを確認できたらjQueryとBootstrapを導入します。

yarn を使っている場合、パッケージをインストールするには、`yarn add` というコマンドを実行します。

**【例】**

```console
yarn add project-name
```

参考：[yarn add](https://classic.yarnpkg.com/ja/docs/cli/add/)

それでは、以下のコマンドを実行してください。

```console
yarn add jquery bootstrap popper.js
```

Bootstrapでは、いくつかのコンポーネントで jQuery, Popper.js といった JavaScript のプラグインが必要なため一緒にインストールします。

コマンドを実行すると、次のような結果が表示されます。

```console
yarn add jquery bootstrap popper.js
yarn add v1.16.0
[1/4] 🔍  Resolving packages...
warning popper.js@1.16.1: You can find the new Popper v2 at @popperjs/core, this package is dedicated to the legacy v1
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning " > webpack-dev-server@3.11.0" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
warning "webpack-dev-server > webpack-dev-middleware@3.7.2" has unmet peer dependency "webpack@^4.0.0".
[4/4] 🔨  Building fresh packages...

success Saved lockfile.
success Saved 3 new dependencies.
info Direct dependencies
├─ bootstrap@4.5.3
├─ jquery@3.5.1
└─ popper.js@1.16.1
info All dependencies
├─ bootstrap@4.5.3
├─ jquery@3.5.1
└─ popper.js@1.16.1
✨  Done in 5.21s.
```

インストールがうまくいっていたら、`package.json` というファイルに以下のようなコードが追加されます。追加されたコードには導入したパッケージとそのパッケージのバージョンが記載されています。

```diff:package.json
{
  "name": "kanban",
  "private": true,
  "dependencies": {
    "@rails/actioncable": "^6.0.0",
    "@rails/activestorage": "^6.0.0",
    "@rails/ujs": "^6.0.0",
    "@rails/webpacker": "4.3.0",
+   "bootstrap": "^4.5.3",
+   "jquery": "^3.5.1",
+   "popper.js": "^1.16.1",
    "turbolinks": "^5.2.0"
  },
  "version": "0.1.0",
  "devDependencies": {
    "webpack-dev-server": "^3.11.0"
  }
}
```

最後に導入したパッケージの設定のコードを追加します。`config/webpack/environment.js` に以下のコードを追加してください。

```diff:config/webpack/environment.js
const { environment } = require('@rails/webpacker')

module.exports = environment

+ const webpack = require('webpack')
+ environment.plugins.append(
+   'Provide',
+   new webpack.ProvidePlugin({
+     $: 'jquery',
+     jQuery: 'jquery',
+     Popper: ['popper.js', 'default']
+   })
+ )
```

上記のコードで`import`や`require`なしで`$`やBootstrapのJavaScriptが使えるようになります。


### Bootstrapのstyleをimport
次に、`app/javascript/stylesheets/application.scss`にBootstrapのstyleをimportする記述を追記します。

この`app/javascript/stylesheets`ディレクトリ及び、`app/javascript/stylesheets/application.scss`ファイルは存在しないので以下のコマンドで作成します。

```console
mkdir app/javascript/stylesheets
touch app/javascript/stylesheets/application.scss
```

作成したら、`application.scss`ファイルに以下のコードを追加してください。

```scss:app/javascript/stylesheets/application.scss
@import '~bootstrap/scss/bootstrap';
```


## application.jsにコードを追加
yarn でインストールしたBootstrapのパッケージを利用できるように`import`します。

次に`app/javascript/packs/application.js` に以下のコードを追加してください。

```diff:app/javascript/packs/application.js
+ import 'bootstrap';
+ import '../stylesheets/application';

// This file is automatically compiled by Webpack, along with any other files
// present in this directory. You're encouraged to place your actual application logic in
// a relevant structure within app/javascript and only use these pack files to reference
// that code so it'll be compiled.

require("@rails/ujs").start()
require("turbolinks").start()
require("@rails/activestorage").start()
require("channels")


// Uncomment to copy all static images under ../images to the output folder and reference
// them with the image_pack_tag helper in views (e.g <%= image_pack_tag 'rails.png' %>)
// or the `imagePath` JavaScript helper below.
//
// const images = require.context('../images', true)
// const imagePath = (name) => images(name, true)
```


## レイアウトに stylesheet_pack_tag を追加
最後にレイアウトに `stylesheet_pack_tag` を追加します。`stylesheet_pack_tag` を使うことでWebpackで`.css`や`.scss`ファイルのスタイルシートにも対応します。

`app/views/layouts/application.html.erb` に以下のコードを追加してください。

```diff:app/views/layouts/application.html.erb
<!DOCTYPE html>
<html>
  <head>
    <title>Kanban</title>
    <%= csrf_meta_tags %>
    <%= csp_meta_tag %>

    <%= stylesheet_link_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>
    <%= javascript_pack_tag 'application', 'data-turbolinks-track': 'reload' %>
+   <%= stylesheet_pack_tag 'application', 'data-turbolinks-track': 'reload' %>
  </head>

  <body>
    <%= yield %>
  </body>
</html>
```

以上でBootstrapの導入は終了です。


## 3. Bootstrapが導入されたか確認
実際にBootstrapが機能するか確認します。

仮のボタンにBootstrapのクラスを当てます。

`app/views/top/index.html.erb`を以下のコードを追加してください。

```
app
└── views
    └── top
        └── index.html.erb
```

```erb:app/views/top/index.html.erb
<p>このページは仮のトップページです。</p>

<%# ここに追加する %>
<%= link_to "仮のボタンです", "#", class: "btn btn-primary" %>
```

コードを追加したら、http://localhost:3000 にアクセスしてください。青色のボタンが表示されていればうまく動作しています。

![image](https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:2500/https://www.filepicker.io/api/file/j2Ntm0ovQcK99BjoDgh1)

以上で今回のパートは終了です。

お疲れ様でした。
