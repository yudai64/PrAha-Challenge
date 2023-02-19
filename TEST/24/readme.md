### 課題１（質問）
#### テスト駆動開発のメリットと、デメリット
***メリット***
- 必要なコードしか書かなくなる
    - 原則に従うと、テストが全てパスしたら本番のコードを書かないようにする必要がある。結果、機能を実装するのに必要なコードのみがプロダクションコードに書かれることになる。
- 疎結合なコードになる
    - テスト可能な状態でコードを書こうとするとするほど、コードの依存性が排除されて、疎結合なコードに近づく。外から振る舞いを変更できるように作られていないと単体テストが書けないため。
- メンテナンスが容易になる
    - 疎結合であると、モジュールの変更が容易にできる。
- リファクタリングが容易
    - 全ての機能がテストされているためリファクタリングがしやすくなる。
- テストと実装を繰り返し行うため、仕様理解が深まる。
- バグを早期に発見できる。

***デメリット***
- テスト駆動開発を習得するまでに時間がかかる。
- チーム全員が採用する必要がある。ユニットテストとTDDプロセスの重要性を認識し、信じなければならない。


#### TDDの用語
***レッド・グリーン・リファクタリング***
- テスト駆動開発のサイクルのこと。これら3つの作業を細かく繰り返して開発を行う。
- レッド
    - テストコードを書く。
    - 実装する機能の要件を適切な粒度に分けて、どんなテストが必要になるかを明らかにする。
    - そのテストは必ず失敗する。
- グリーン
    - 機能の実装を行う。
    - 先に書いたテストコードを全てパスできる最小限のコードを書く。
- リファクタリング
    - リファクタリングを行う。
    - 成功しているテストが成功しているままで、コードを綺麗にしていくこと。
    - プロダクトコードもテストコードも含む。

***三角測量***
- 同じ対象に対して違う観点のテストを追加して、プロダクションコードが正常に動作するかどうかを測ること

***仮実装***
- テストをパスさせることを目的にした最低限の実装のこと。
- 「動作するコード」を最短で書く。

#### Behavior Driven Development（行動駆動開発）
- TDDは小さな機能の断片を分離してテストすることに重点を置いているのに対して、BDDはエンドユーザーの立場からアプリケーションの動作をテストするよう設計されている。
- BDDでは、開発者以外にもプロダクトマネージャー、テストエンジニアが協力し、望ましい機能の具体例を考える。
    - テストの内容は開発者以外にも理解できるものであり、外部からのフィードバックを得れる。

### 課題２（実装）
[こちら参照](https://github.com/yudai64/jestSample/commit/f630605bef6617df1327ed49f4a893ac2b4ba4b5)

### 参考
- [Advantages and disadvantages of Test Driven Development (TDD)](https://www.geeksforgeeks.org/advantages-and-disadvantages-of-test-driven-development-tdd/)
- [TDD Boot Camp 2020 Online #1 基調講演/ライブコーディング](https://www.youtube.com/watch?v=Q-FJ3XmFlT8)
    - 52:24 テスト容易性
- [テスト駆動開発って何だろう](https://dev.classmethod.jp/articles/what-tdd/)
- [What is BDD and Why?](https://medium.com/codeops/what-is-bdd-and-why-936e80bce511)
- [What is BDD? An Introduction to Behavioral Driven Development](https://blog.testlodge.com/what-is-bdd/)
- [TDD vs BDD – What’s the Difference Between TDD and BDD?](https://blog.testlodge.com/tdd-vs-bdd/)
- [Understanding the Differences Between BDD & TDD](https://cucumber.io/blog/bdd/bdd-vs-tdd/)
