# nuxt-labo
## 概要
nuxt.jsの実験環境です。

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

### axiosの実装
1. axios のインストール　※プロジェクト作成時に選択している場合は不要。
```
npm install --save @nuxtjs/axios
```
--saveをつけることで、自動的にpackage.jsonに追加してくれる。

2. nuxt.configに設定を追加
```
  modules: [
    ['@nuxtjs/axios'],
  ],
```

3. 呼出処理を記述

### 参照URL
[Nuxt.jsでaxiosの使い方と設定方法を紹介](https://ma-vericks.com/nuxt-axios/)