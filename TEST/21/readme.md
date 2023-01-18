### 課題1

***スナップショットテストとは***
- コンポーネントで作成するUIが、前回テスト実行時と変わっていないかをチェックするテスト
- UIが予期せず変更されていないかを確かめることができる

***防止できる不具合***
- あるコンポーネントの変更による他のコンポーネントの(UIに関する)不具合
- 他思いつかずでした。。。

***防止できない不具合***
- クリックなどのイベント処理に含まれる不具合
- 前回のスナップショットがない場合の不具合
- 前回作成時のスナップショット時から存在する不具合


### 課題2
[こちら参照](https://github.com/yudai64/react-tutorial)

***作成されたスナップショットを見てみましょう。どんな情報が記載されているでしょうか？***
- story ごとに、レンダリングされた内容が記載されている
- イベントは[Function]として記載されている

### 課題3
- (スタイルをコンポーネントとは別ファイルで管理しているとした場合)
    - スタイルが更新された場合、スナップショットは更新されるでしょうか。
- jest でスナップショットを実行する際
    - 失敗したすべてのスナップショットを再作成するオプションはなんでしょうか。
    - またどのスナップショットケースが再作成されるかを制限したい場合、どのオプションを指定すれば良いでしょうか。





---

### 参考
- [Jest再入門 - スナップショットテスト編](https://developer.mamezou-tech.com/testing/jest/jest-snapshot-testing/)
- [Storyshotsを止めてスナップショットテストの仕組みを自作した話](https://www.wantedly.com/companies/wantedly/post_articles/421107)
- [Creating snapshots in Jest for testing React applications](https://circleci.com/blog/snapshot-testing-with-jest/)
- [Snapshot Testing: Benefits and Drawbacks](https://www.sitepen.com/blog/snapshot-testing-benefits-and-drawbacks)
- [Snapshot Testing](https://jestjs.io/docs/snapshot-testing)