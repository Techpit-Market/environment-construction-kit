> 
>
> 
>
> 
>
> ここから教材

# 新規Vueプロジェクトの作成
JavaScriptのフレームワークである**Vue.js**環境のプロジェクトを作成し、Webアプリケーションを開発する環境を構築します。

今回は**Vue.js 3系**の環境構築を行います。

Vue.js 3系は、LTS（Long Term Support）と呼ばれる、長期サポートが保証されている最新のバージョンです(2021年10月現在)。

## プロジェクトの作成
Vue.js環境のプロジェクトディレクトリを作成し、Webアプリケーションを作成するためのベースとなる環境を構築します。

プロジェクトディレクトリはお好きな場所に作成することができます。

あらかじめ、`cd`コマンドを用いて、プロジェクトディレクトリを置きたい場所に移動してください。

ホームディレクトリに作成する場合は以下のコマンドで移動できます。

```console
cd ~
```

前回のパートでも紹介したように、VueCLIではコマンドライン上で選択肢に回答していくだけで簡単にプロジェクトが作成できます。

プロジェクトの作成は `vue create` コマンドを使用して行います。

本教材では「**〇〇**」という名前のアプリケーションを作成します。

以下のコマンドを実行してください。

```console
vue create 〇〇
```

コマンドを実行すると選択肢が表示されるので、1つずつ解説していきます。

### プリセットの選択
プリセットとは、前もって用意されている設定のことで、プリセットを使用することで、以前作成した環境と同じ設定で環境構築をすることができます。

VueCLIではあらかじめ2つのプリセットが用意されていますが、今回は手動で設定を行なうので、「Manually select features」を選択してください。

キーボードの上下キーでカーソル(`❯`)を移動し、エンターキーを押すことで決定することができます。

```
Vue CLI v4.5.14
? Please pick a preset: (Use arrow keys)
  Default ([Vue 2] babel, eslint) 
  Default (Vue 3) ([Vue 3] babel, eslint) 
❯ Manually select features 
```

### 機能とツールの選択
プロジェクトで必要となる機能やツールを選択します。

今回は以下の機能とツールを選択します。

|機能・ツール|説明|
|--|--|
|Choose Vue version|Vue.jsのバージョンを指定する|
|Babel|JavaScriptの最新版であるES6等の新しい文法をES5に変換するコンパイラ|
|Linter / Formatter|`Linter`はあらかじめ決められたルールに沿ってコードが記述されているかをチェックするツール。`Formatter`はコードを決められたルールに従って自動整形するツール。|

上記の3つの項目にチェックを入れて次へ進みます。

キーボードのスペースキーチェックのON/OFFを切り替え、エンターキーを押すことで決定することができます。

```
? Check the features needed for your project: (Press <space> to select, <a> to toggle all, <i> to invert selection)
❯◉ Choose Vue version
 ◉ Babel
 ◯ TypeScript
 ◯ Progressive Web App (PWA) Support
 ◯ Router
 ◯ Vuex
 ◯ CSS Pre-processors
 ◉ Linter / Formatter
 ◯ Unit Testing
 ◯ E2E Testing
```

### Vue.jsのバージョンの選択

今回はVue.js 3系を使用するので、「3.x」を選択してください。

```
? Choose a version of Vue.js that you want to start the project with (Use arrow keys)
  2.x 
❯ 3.x 
```

### Linter / Formatter の選択
Linter / Formatter の設定を選択します。

今回はESLintというLinterのみ使用するよう設定するので、「ESLint with error prevention only」を選択してください。

```
? Pick a linter / formatter config: (Use arrow keys)
❯ ESLint with error prevention only 
  ESLint + Airbnb config 
  ESLint + Standard config 
  ESLint + Prettier 
```

### Linter実行タイミングの選択
Linterをいつ実行するのかを選択します。

ファイルを保存したタイミングとgitのコミットを行なったタイミングを選択でき、両方選択することもできます。

今回はファイルを保存したタイミングでのみLinterを実行したいため、「Lint on save」にのみチェックを入れて次へ進みます。

```
? Pick additional lint features: 
 ◉ Lint on save
❯◯ Lint and fix on commit
```

### 設定ファイルの選択
BabelやESLintの設定を`package.json`というファイルで行なうか、ツールごとに専用のファイルで行なうかを選択します。

今回はツールごとに専用のファイルで設定するので、「In dedicated config files」を選択してください。

```
? Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)
❯ In dedicated config files 
  In package.json 
```

### プリセットの保存
ここまで行なった設定をプリセットとして保存するかどうかを選択します。

今回は次回の環境構築でも使い回せるようにプリセットとして保存します。

`y`と入力して、エンターキーを押してください。

```
? Save this as a preset for future projects? (y/N) y
```

続いて、プリセット名を入力します。

どのような名前でも構いませんが、ここでは`my-preset`という名前で保存します。

`my-preset`と入力し、エンターキーを押してください。

```
? Save preset as: my-preset
```

### パッケージマネージャの選択
パッケージをどのツールで管理するかを選択します。

今回は`npm`でパッケージを管理するため、「Use NPM」を選択して、エンターキーを押してください。

なお、以前にVueCLIでVue.jsの環境構築をしたことがある場合は、この設問が表示されないことがあります。

```
? Pick the package manager to use when installing dependencies: (Use arrow keys)

  Use Yarn
❯ Use NPM
```

### プロジェクトの作成
ここまで行なった設定を踏まえて、Vue.jsのプロジェクトが作成されます。

以下のように、「Successfully created project vue-sample.」と表示されれば、プロジェクトの作成は完了です。

```
🎉  Successfully created project vue-sample.
👉  Get started with the following commands:

 $ cd vue-sample
 $ npm run serve
```
## Vue.jsアプリケーションの実行
プロジェクトが作成できたら、Vue.jsアプリケーションを立ち上げ、ブラウザにVue.jsの初期画面を表示させてみましょう。

まずは作成したプロジェクトディレクトリへ移動しましょう。

以下のコマンドを実行してください。

```console
cd 〇〇
```

プロジェクトディレクトリへ移動できたら、Vue.jsアプリケーションを立ち上げます。

以下のコマンドを実行してください。

```console
npm run serve
```

コマンドを実行すると以下のようなメッセージが表示されます。

```
 DONE  Compiled successfully in 1592ms                                                                                                                                                                                        21:20:58


  App running at:
  - Local:   http://localhost:8080/ 
  - Network: http://192.168.1.6:8080/

  Note that the development build is not optimized.
  To create a production build, run npm run build.
```

Vue.jsアプリケーションを起動したら、ブラウザで「 http://localhost:8080/ 」にアクセスします。

次の画像のようにVue.jsのデフォルトページが表示されていれば、うまく動作しています。

<img src="" width="1000">

以上で今回のパートは終了です。

お疲れさまでした。
