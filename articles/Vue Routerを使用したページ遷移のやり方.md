Vue Routerを使用したページ遷移のやり方

初心者向け Vue.js vue-router JavaScript

##はじめに
Vue.jsを使った、ページの切り替え方法について解説していきます。
Vueの開発環境の構築は終わったけど、何か知らないファイルたくさん入ってるし、どこをどういじって開発していけばいいのかわからない！といった方向けの記事となります。

開発環境の構築はこちらから
[初心者向け！Vue.jsの開発環境の構築](https://qiita.com/Mitsuzara/items/4dea8c0aa95d6284980a)

##表示させたいページの作成
ここではhome.vueを表示させてみます。
まずはsrc/components/home.vueを新たに作成します。

```home.vue
<template>
  <div>
    <p>ようこそ！<br/>ここは私のサイトです</p>
  </div>
</template>
<script>
export default {
  name: 'Home',
}
</script>
```
##ルーティング設定
ページの作成が終わったので、次はRouterの設定をしましょう。
src/router/index.jsを開いて、新しく作成したhome.vueをルーティングさせます。{} や , を忘れないようにしましょう。

```index.js
import Vue from 'vue'
import Router from 'vue-router'
import HelloWorld from '@/components/HelloWorld'
import Home from '@/components/home' // new add

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'HelloWorld',
      component: HelloWorld
    },                 // , の追加を忘れずに
    {
      path: '/home',   // new add
      name: 'Home',    // new add
      component: Home  // new add
    }
  ]
})
```
これでokです。yarn devで立ち上げて [localhost:8080/home/](http://localhost:8080/home/) にアクセスしてみましょう。
![localhost_8080_ (1).png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/459087/1ef2c1b3-160c-fdc3-b115-f3133dae94aa.png)
home.vueで作成したhomeページを表示できました。

##アドレスバーの # を消したい
<img width="500" alt="スクリーンショット 2019-07-23 9.57.57.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/459087/25484dbe-77a1-6a9f-79a6-e427184f9e84.png">
アドレスバーに # が付いているのに気がつきましたか？これは消す事ができます。先ほどのsrc/router/index.jsにコードを追加します。

```index.js
import Vue from 'vue'
import Router from 'vue-router'
import HelloWorld from '@/components/HelloWorld'
import Home from '@/components/home'

Vue.use(Router)

export default new Router({
  mode: 'history',  // new add
  routes: [
    {
      path: '/',
      name: 'HelloWorld',
      component: HelloWorld
    },
    {
      path: '/home',
      name: 'Home',
      component: Home
    }
  ]
})
```
再度アドレスバーに [localhost:8080/home/](http://localhost:8080/home/) と入力してみましょう。
<img width="500" alt="スクリーンショット 2019-07-23 9.56.45.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/459087/5944d972-df68-2d67-6b36-981bba97d952.png">
# が表示されなくなっているのを確認できました。

##まとめ
ここまで読んでくださりありがとうございます。
上手くいきましたか？何か不明な点がございましたら、コメント等頂けましたら幸いです。
ページを作成し、そのページを表示する為にルーティング設定をする。これはVueで開発する上で必須の知識となるので覚えておきましょう。
ちなみにnuxt.jsだと、この様なルーティング設定が不要でファイル名がそのままURLになるので非常に楽です。興味がある方は調べてみてください。
