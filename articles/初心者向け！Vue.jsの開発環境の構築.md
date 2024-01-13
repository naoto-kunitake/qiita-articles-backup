初心者向け！Vue.jsの開発環境の構築

Vue.js 初心者向け 環境構築 JavaScript

## はじめに
ここでは、`vue cli`を利用した`Vue.js`開発環境の構築を行っていきます。
すでにプログラミング経験が豊富な方は、公式のドキュメントを読んだりして問題なく環境構築ができると思います。しかしプログラミング未経験・新人エンジニアの方は環境構築だけでつまずいてしまうこともある事でしょう。参考にしている記事が古ければコマンドをマネしても上手くいかない事があり頭を抱えることも…そんな方たちに向けた記事となります。
筆者の環境は`mac`です。`windows`の方はもしかしたらどこかでエラーが出てしまうかもしれません。その場合コメント等で教えていただければ、今後見てくれる方の為に記事を修正致します。
では、`Vue.js`の環境構築をやっていきましょう。


## まずは準備
今回Vueのインストールには`yarn`を使用します。
yarnのインストールにはnpmが必要で、npmの使用にはnode.jsのインストールが必要です。
必要な物を順番に揃えていきましょう。

まずはnode.jsをインストール。
https://nodejs.org/en/
こちらからダウンロードします。ダウンロード前にOSが間違っていないか注意しましょう。

node.jsをインストールすると、npmも一緒にインストールされます。以下のコマンドで確認してみましょう。

```:ターミナル
$ node -v # node.jsのバージョン確認
v10.15.3

$ npm -v # npmのバージョン確認
6.4.1
```

確認できました。
では続いてyarnをインストールしますが、windowsかmacかでちょっと方法が変わります。

macの方はこちら。brewコマンドが使えない方はHomebrew ( https://brew.sh/index_ja ) をインストールしてください。

```:ターミナル
$ brew update
$ brew install yarn
```

windowsの方はこちらから
https://yarnpkg.com/lang/ja/docs/install/#windows-stable
一番上のインストーラをダウンロードし、起動するとコマンドを叩く事なくyarnをインストールできます。下二つの方法でももちろん構いません。お好みでどうぞ。

正常にインストールされたか確認します。

```:ターミナル
$ yarn -v # yarnのバージョン確認
1.16.0
```

確認できました。これで準備は終了です。vueをインストールしていきましょう。


## アプリケーションプロジェクトの作成
アプリケーションプロジェクトっていきなりよくわからない単語が出てきましたが、これから作るアプリのディレクトリ(フォルダ)を作るよ！的な意味です。
さっそくやっていきましょう。
まずはこの二つのコマンドをターミナルで打ち込んでください。

```:ターミナル
$ yarn global add @vue/cli
$ yarn global add @vue/cli-init
```

これでVueの最新版がインストールされたはずです。確認してみましょう。

```:ターミナル
$ vue --version # vue.jsのバージョンを確認
3.9.2
```

最新版のVueがインストールされていることが確認できました。
続いてプロジェクト作成を行います。ここでは、`vue-app`というプロジェクト名で作成します。

```:ターミナル
$ vue init webpack vue-app
```

色々聞かれるはずです。何を聞かれているのかは今回割愛しますが、意味がわからない内はエンターキー連打で問題ありません。もちろん、後から`package.json`をいじることで変更することも可能なので安心しましょう。
全ての質問に答えるとインストールが始まります。インストール終了後、以下のような内容が出力されます。これで開発環境の構築は終了です。

```:ターミナル
Running eslint --fix to comply with chosen preset rules...
# ========================


> vue-app@1.0.0 lint D:¥vue-app
> eslint --ext .js,.vue src test/unit test/e2e/specs "--fix"


# Project initialization finished!
# ========================

To get started:

  cd vue-app
  npm run dev

Documentation can be found at https://vuejs-templates.github.io/webpack
```

## アプリケーションの起動確認
`vue cli`を使用してアプリケーションプロジェクトの作成が終わりました。構築が正常に完了しているかどうか確認の意味も兼ねて、起動してみましょう。
まずは作成したアプリケーションプロジェクトへ移動します。

```:ターミナル
$ cd vue-app
```

続いて必要な依存モジュールをインストールします。

```:ターミナル
$ yarn install
```

最後に開発モードでアプリケーションを起動します

```:ターミナル
$ yarn dev
```

次のような内容の出力がされたと思います。

```:ターミナル
 DONE  Compiled successfully in 2820ms                                                          10:39:56

 I  Your application is running here: http://localhost:8080
```

ブラウザを開いて、出力に記載されている[localhost:8080](http://localhost:8080)を入力してみましょう。
![localhost_8080_.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/459087/d7fc0752-0589-27a9-49e3-8c881f818ddf.png)
この画面が表示されたら無事、環境構築が終了しています。
お疲れさまでした。
