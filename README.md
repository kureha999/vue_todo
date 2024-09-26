# Start!
``` bash:bash
$ npm create vue@latest

✔ Project name: … vue_todo
✔ Add TypeScript? … No 
✔ Add JSX Support? … No 
✔ Add Vue Router for Single Page Application development? … No 
✔ Add Pinia for state management? … No 
✔ Add Vitest for Unit Testing? … No 
✔ Add an End-to-End Testing Solution? › No
✔ Add ESLint for code quality? … Yes
✔ Add Prettier for code formatting? … Yes
✔ Add Vue DevTools 7 extension for debugging? (experimental) … Yes
```


# 概要
### TODO-appの作成
###### 機能
* タスクの追加(内容,期限を入力)
* タスクの編集(内容,期限,ステータスを編集できる)
* タスクの削除(一個ずつ選んで消せる)

###### タスクの保存先
> 今回は、ローカルストレージを使用する。
* ローカルストレージとは、ブラウザ上にデータを保存する方法。
* データベースを用意しないでデータを操作できる。
* [key]と[value]の組み合わせで文字列を保存できる
> 今回の様に配列やオブジェクトを扱うには、JSONデータとして文字列に変換する必要がある。

* データを取得 - getItem(key)
* データを保存 - setItem(key,value)
* データを削除 - removeItem(key)
```
例)
localStorege("message", "ローカルストレージに保存");
```
> ローカルストレージの状態は、検証ツールの[Application]タグで確認


### 補足
create-vueだけでは、必要なパッケージを ***package.json*** に羅列しただけなのでinstallしないといけない
installされはパッケージは、 ***node_module*** に入る。
```
npm install
```
起動の仕方
```
npm run dev
```
開発が終わってリリースするときにする(distフォルダを作成)
```
npm run build
```
distフルダが正しく動いているか確かめる
```
npm run preview
```

コードを修正してくれる
```
npm run lint
```
コードを綺麗にフォーマットしてくれる
```
npm run prrita
```


