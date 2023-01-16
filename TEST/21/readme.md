### 課題1

***スナップショットテストとは***
- コンポーネントで作成するUIが、前回テスト実行時と変わっていないかをチェックするテスト
- UIが予期せず変更されていないかを確かめることができる

***防止できる不具合***
- あるコンポーネントの変更による他のコンポーネントの(UIに関する)不具合
- 
- 

***防止できない不具合***
- クリックなどのイベント処理に含まれる不具合
- 前回のスナップショットがない場合の不具合
- 前回作成時のスナップショット時から存在する不具合


### 課題2
[こちら参照](https://github.com/yudai64/react-tutorial)


---

### 参考
- [Jest再入門 - スナップショットテスト編](https://developer.mamezou-tech.com/testing/jest/jest-snapshot-testing/)
- [Storyshotsを止めてスナップショットテストの仕組みを自作した話](https://www.wantedly.com/companies/wantedly/post_articles/421107)
- [Creating snapshots in Jest for testing React applications](https://circleci.com/blog/snapshot-testing-with-jest/)
- [Snapshot Testing: Benefits and Drawbacks](https://www.sitepen.com/blog/snapshot-testing-benefits-and-drawbacks)