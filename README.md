# nuxt-labo

## 概要

nuxt.js の実験環境です。

## メモ

### プロジェクト作成手順

1. プロジェクト作成

```
npm init nuxt-app <project-name>
```

2. プロジェクト起動

```
npm run dev
```

### axios の実装

1. axios のインストール　※プロジェクト作成時に選択している場合は不要。

```
npm install --save @nuxtjs/axios
```

--save をつけることで、自動的に package.json に追加してくれる。

2. nuxt.config に設定を追加

```
  modules: [
    ['@nuxtjs/axios'],
  ],
```

3. 呼出処理を記述

#### 参照 URL

[Nuxt.js で axios の使い方と設定方法を紹介](https://ma-vericks.com/nuxt-axios/)

### a タグと NuxtLink の違い

a タグは外部ページ、NuxtLink は内部ページで使う。

-   NuxtLink を使う利点  
    公式によるとパフォーマンスが高まるらしい。

### asyncData メソッドについて

-   asyncData 内では「this(コンポーネントのインスタンス)」にアクセスできない。
-   page レベルのコンポーネントにのみ使用可能。

### 非同期通信で困ったこと

[javascript this 使用時にエラー「Uncaught TypeError: Cannot set property ‘xxx’ of undefined」が発生した場合](https://mebee.info/2021/03/24/post-26109/)

### Prettier の使い方

[prettier の使い方](https://qiita.com/kiida/items/405bb07c4b52bfee0219)
[【Prettier】「なんとなく使う」から「分かって使う」へ【Visual Studio Code】](https://ai-can-fly.hateblo.jp/entry/prettier-usage)

CIはあくまで異常を検知するもの。  
prettierのコマンドを走らせてもいいが、引っ掛かった場合は、当人に修正してもらうらしい。

### yarnとnpm
どっちもpackage.jsonを見てるが、yarnはyarn.lockを新たに作るよ。