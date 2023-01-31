### 課題1
- Cypressの実装は[こちら参照](https://github.com/yudai64/react-tutorial)
- すみません、引き分けの場合のstorybook来週までに追加します。。！

***なぜカスタム属性を追加する必要があるか***
- CSS attributes や テキストに比べて、変更される可能性が低いため
- https://docs.cypress.io/guides/references/best-practices#Selecting-Elements

***Container/Presentationalパターン***
- ロジックとUIを分けて実装することで関心の分離を図るフロントエンドのデザインパターン
    - Container Component はロジックを責務とする
    - Presentational Component は UI を責務とする

- hooksによって陳腐化している(?)

### 課題2
***E2Eテストのメリットとデメリット***
- メリット
    - アプリケーションに対して高い信頼性が持てるようになる
- デメリット
    - メンテナンスのコストがかかる
    - 実行時間が長い

***テスト手法（単体、統合、E2Eなど）を選択する基準***
- 組み合わせて使用するべき
- コストの高さ
    - 単体 < 結合 < E2E
    - E2Eテストは失敗するポイントが増えるため、テストが壊れ安くなり、テストの解析と修正にかかる時間が長くなる
- 実行にかかる長さ
    - 単体 < 結合 < E2E
    - E2Eテストは実行時間が長い
- 信頼性の高さ
    - 単体 < 結合 < E2E
    - E2Eテストは、想定されるシナリオを実際にテストできるので信頼性が高い
        - より多くのコードも実行されることも信頼性につながる


***E2Eテストでは、どのような要素を指定すればテストが壊れにくくなるか***
- 変更されにくい要素を指定する
    - data属性

### 課題3
[こちら参照](https://github.com/yudai64/react-tutorial)

### 課題4
- cypressでテストの結果が失敗する場合、failという結果が出るまで4秒ほどかかりますが何故でしょうか。


---
### 参考
- [Static vs Unit vs Integration vs E2E Testing for Frontend Apps](https://kentcdodds.com/blog/static-vs-unit-vs-integration-vs-e2e-tests)