### 課題1
[レポジトリ](https://github.com/yudai64/react-tutorial)

### 課題2
[こちら参照](https://github.com/yudai64/react-tutorial/commit/d3c7032b64e2fffbbd4e283d5b40f376e9c77698)

### 課題3

***メリット***
- 本番環境のコードを変更せずに、様々な条件によるUIの確認を行うことができる
- ドキュメント化されていることで、
    - 重複したコンポーネントを作成してしまうことを防ぐ
    - コンポーネントの仕様を理解しやすくなる
- コンポーネント単位でUIのテストをすることができる
- デザイナーとデザインを簡単に共有できる

***デメリット***
- コンポーネントを修正した場合、storybookも更新する必要がある
    - 作業が増える
    - 更新を忘れると本番のコードと乖離してしまう
- プロジェクトの途中で入れると実装が面倒そう
- バグがあるアドオンもあるらしい

### 課題４（クイズ）
- argsの設定値は他のstoriesのファイルでも使用できる。正しい？
- Decorators はどのような目的で使用されるでしょうか
- storyとして読み込んでほしいファイル名の規則を変更したい場合、どこで設定すれば良いでしょうか