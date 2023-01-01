### 課題2
[こちら参照](https://github.com/yudai64/jestSample/tree/main/__tests__)


### 課題3
***なぜ元の関数はカバレッジ100%のテストを書けなかったか***
- `database.save()`, `nameApiService.getFirstName()`, `axios.get()`の戻り値が予測できず、テスト実行毎に結果が違う可能性があるため
  - 冪等性が保証されない
  - 実装に依存している状態

***依存性の注入とは？どのような問題を解決するために使われる？***
- あるコードが必要とするオブジェクトを、コード内で作成するのではなく外部で作成して渡すこと
- 結合度が高くなってしまうことや、テストがしにくいという問題を解決する

***依存性の注入を実施することで、モジュール同士の結合度の強さはどのように変化した？***
- 結合度は弱くなった
  - 外部結合 → スタンプ結合。。？

***単体テストで外部サービスとの通信が発生すると、どのようなデメリットがあるでしょうか***
- 外部サービスが落ちている場合、テストも失敗してしまう
- リクエストに時間がかかる
- テスト毎にリクエストしていると相手のサービスに負荷がかかってしまう
  - リクエスト制限かけられるかも？

***Property Based Testing***
- 定義された条件に合わせて自動生成された膨大な値に対してテストを行う手法
- 普段テストを書くときはカバレッジを指標とすることが多く、1ケースあたりのテストパターンは限られた数になるが、Property Based Testingを使用することで大量のパターンをテストできる。エッジケースを見つけることができるかもしれない

***単体テストケースを増やしても可読性、保守性、実行速度などに問題が起きないよう工夫できること***

***可読性***
  - arrange-act-assertパターンを採用する
> オブジェクトを “配置 (Arrange)” し、必要に応じて作成および設定します。
> オブジェクトを操作 (Act) します。
> 何かが想定どおりであることをアサート (Assert) します。

  - テスト名の命名に気を付ける
> テストの名前は、次の 3 つの部分で構成される必要があります。
> テスト対象のメソッドの名前。
> それがテストされるシナリオ。
> シナリオが呼び出されたときに想定される動作。

***保守性***
- それぞれのテストを独立させる
  - 別のテストに依存しないように書く

***実行速度***
- 並列でテストを実行する


### 課題4
***関数を3つ作成***

[こちら参照](https://github.com/yudai64/jestSample/blob/main/functions.ts#L44)

***jestに関するクイズを作成***
1. 以下のテストは成功する。正しい？
```
test(‘0.1 + 0.2 = 0.3’, () => {
  expect(0.1 + 0.2).toEqual(0.3)
})
```

2. 以下のテストは成功する。正しい？
```
class Human {
  private name: string
  constructor(name: string) {
    this.name = name
  }
}
test(‘are note semantically the same’, () => {
  expect(new Human(‘taro’)).toEqual({ name: ‘taro’ })
})
```

3. 以下のテストは成功する。正しい？
```
test("toEqual", () => {
    expect(1).toEqual("1");
});
```

### 課題5
- ダミーデータを作成する`@faker-js/faker`というものがある
  - https://github.com/supabase/supabase/blob/master/tests/features/javascript/authAdmin.spec.ts#L2

- スナップショットテストというものがある。コンポーネントが生成するUIが前回実行時と変わっていないかをチェックするみたい
  - https://github.com/prisma/prisma/blob/main/packages/cli/src/__tests__/artificial-panic.test.ts#L33
    - https://developer.mamezou-tech.com/testing/jest/jest-snapshot-testing/
    - インラインスナップショットのマッチャーを使うとコードが直接書き換わる

- `test.concurrent`を使用することでテストを並列に実行できる

---
### 参考
- [fast-check で Property Based Testing を試してみる](https://zenn.dev/ryo_kawamata/articles/22d4408bd1f138)
- [.NET Core と .NET Standard での単体テストのベスト プラクティス](https://learn.microsoft.com/ja-jp/dotnet/core/testing/unit-testing-best-practices)
- [xUnit Test Patternsから学ぶ12個のユニットテストの原則](https://qiita.com/hgsgtk/items/a3186a250d36d3b224d9)
- [食べチョクの自動テスト実行速度を2倍以上速くした](https://tech.tabechoku.com/entry/2022/07/07/123000)
- [Jest再入門 - スナップショットテスト編](https://developer.mamezou-tech.com/testing/jest/jest-snapshot-testing/)