## バージョンの確認【Ruby編】

この章では、RubyおよびRuby on Railsのバージョンを確認していきます。

なお、この教材ではRubyのバージョンは○○、Ruby on Railsのバージョンは○○を推奨しています。

>↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑
>○○に教材のバージョンを入れる

※Cloud9は環境ごとに設定が異なります。一度環境を削除した場合は再度バージョンの指定などをしなくてはいけないことを留意してください。

### Rubyのバージョンを確認する

以下のURLからコンソールにサインインして、Cloud9を立ち上げましょう。

https://us-east-2.console.aws.amazon.com/console/

Cloud9上のTerminalを立ち上げて、以下のコマンドを実行してRubyのバージョンを確認しましょう。

```bash
$ ruby -v
``

以下のように数字が表示されます。
ここではRubyの環境が「**2.6.3**」であることがわかります。

```bash
$ ruby -v
ruby 2.6.3p62 (2019-04-16 revision 67580) [x86_64-linux]
```

### Rubyのバージョンを変更する

それではここからRubyのバージョンを変更していきます。

Rubyのバージョン管理ツールであるrvmを使います。

以下のコマンドでインストール済みのRubyのバージョンを確認します。

```bash
$ rvm list
```

以下のコマンドでインストール可能なRubyのバージョンを一覧表示します。

```bash
rvm list known
```

実行結果で、自分のインストールしたいバージョンがあることを確認してください。

```bash
rvm list known

//====略====

# MRI Rubies
[ruby-]1.8.6[-p420]
[ruby-]1.8.7[-head] # security released on head
[ruby-]1.9.1[-p431]
[ruby-]1.9.2[-p330]
[ruby-]1.9.3[-p551]
[ruby-]2.0.0[-p648]
[ruby-]2.1[.10]
[ruby-]2.2[.10]
[ruby-]2.3[.8]
[ruby-]2.4[.6]
[ruby-]2.5[.5]
[ruby-]2.6[.3]
ruby-head

//====略====

```

次に、以下のコマンドを実行してRubyのバージョンをインストールします。

`<version>`の部分には、インストールするバージョンを指定してください。

```bash
$ rvm install <version>
```

以下のように表示されれば正常にインストールされています。

ここでは`2.5.5`を指定しています。

```bash
$ rvm install 2.5.5
//===略===
ruby-2.5.5 - #setup
ruby-2.5.5 - #gemset created /home/ec2-user/.rvm/gems/ruby-2.5.5@global
ruby-2.5.5 - #importing gemset /home/ec2-user/.rvm/gemsets/global.gems..................................
ruby-2.5.5 - #generating global wrappers.......
ruby-2.5.5 - #gemset created /home/ec2-user/.rvm/gems/ruby-2.5.5
ruby-2.5.5 - #importing gemsetfile /home/ec2-user/.rvm/gemsets/default.gems evaluated to empty gem list
ruby-2.5.5 - #generating default wrappers.......
```

以下のコマンドで使用するバージョンを指定しましょう。

```bash
$ rvm use <version>
```

最後に以下のコマンドで、先ほど指定したバージョンが表示されることを確認してください。

```bash
$ ruby -v
ruby 2.5.5p157 (2019-03-15 revision 67260) [x86_64-linux]
```

以上でRubyのバージョン変更は終了です。




