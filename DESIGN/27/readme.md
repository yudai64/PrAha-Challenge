### 課題1
***エンティティ***
- ドメインモデルを実装するドメインオブジェクトの1つ。
- 属性ではなく、同一性によって認識されるオブジェクト。
- 可変である。

***値オブジェクト（バリューオブジェクト）***
- ドメインモデルを実装するドメインオブジェクトの1つ。
- システムに登場する金銭や単価といった値をオブジェクトとして定義したもの。
- 等価性によって比較される。
- 不変である。
- 交換が可能である。

***集約***
- データを変更するための単位として扱われるオブジェクトの集まり。
- 境界
    - 集約に何が含まれるかを定義するための境界。
- ルート
    - 集約内部への操作を制限するために、全ての操作はルート越しに行われる。

***ユビキタス言語***
- プロジェクトにおける共通言語。
- ドメインエキスパートと開発者、また開発者同士での言葉の認識の齟齬や翻訳コストをかけないことが目的。

***境界づけられたコンテキスト***
- 特定のモデルを定義・適用する境界を明示的に示したもの。
- 大規模システムのドメインモデルの完全な統合は実現不可能で、費用対効果が低い。そこで、大きなシステムを「境界づけられたコンテキスト」に分割し、それぞれの中でモデル、言語の統一を目指す。
- [境界づけられたコンテキスト 概念編 - ドメイン駆動設計用語解説 [DDD]](https://little-hands.hatenablog.com/entry/2017/11/28/bouded-context-concept)

***ドメイン***
- プログラムを適用する対象となる領域

***ドメインサービス***
- システムにはエンティティや値オブジェクトに記述すると不自然になってしまう振る舞いがある。不自然さを解消するために、その振る舞いの定義を移す先のオブジェクト。

***リポジトリ***
- データに関する処理を分離させたもの。
- データの永続化と再構築を行う。

***アプリケーション（ユースケース層と呼ばれることも）***
- ドメインオブジェクトが行うタスクを管理し、利用者の問題を解決するように導くもの。


***CQS/CQRS（似ているため、違いを重点的に調べてみましょう）***
- CQS
    - コマンドクエリ分離原則(Command-Query Separation:CQS)
- CQRS
    - コマンドクエリ責務分離原則(Command-Query Responsibility Segregation:CQRS)
- CQSとCQRSの違いはメソッドの分離かモデルの分離かという観点
    - https://qiita.com/hirodragon/items/6281df80661401f48731

***DTO***
- データ転送用オブジェクト
> DTOはデータの集合とその読み書き手段のみからなるシンプルなオブジェクトで、そのデータを利用して行われる具体的な処理（ビジネスロジックなど）は含まない。同じプログラミング言語や実行環境などで動作するプログラム間で、データを効率よく、かつ、互いに利用しやすい形式で受け渡す手段としてよく用いられる。 [IT用語辞典](https://e-words.jp/w/DTO.html)

***ドメインモデル貧血症***
- ドメインモデルに書かれているロジックが少なく、その代わりにサービスオブジェクトに書かれている状態。データのためだけにドメインモデルを使っている。
- [ドメインモデル貧血症](https://bliki-ja.github.io/AnemicDomainModel/)

### 課題2
***境界づけられたコンテキスト***
ECサイト
「ユーザー」という概念でも注文時と発送時でコンテキストを分ける

***「Human」エンティティ***
- [このコード](https://www.typescriptlang.org/play?#code/MYGwhgzhAEASCuBbMA7aBvAUNH1gHsUIAXAJ3mGP1IAoAHeAIxAEthpSBTMAE0JACe0FjwBc0EqRYoA5gBpoDZmw7c+KQdGb58PYgLqdxk6fMVNW7Lr35DGLUsQAWPMMSPQAIm84Kll1RsNIRQwRA8TWQBKDGxceJYAM2gaAEJnFggAOgA3MFYeAAVSfDoIGnQROW1dfUNqh2dXdzlQ8IBfKJj0aGcSgHdoFE5BgFFSEtoAcmk8gsUSuimY9ricVbWFljz3aDmRYtLyukWIcUqxCTJTBRq9Awjr2VvGlx9xbxahsMepWU7xIwdCBuGgsPF4lxiPBSGgMtl9jwAJI8einLIiGIAMixvScmVy+REACEQDp7oY0Ucsnc6pxsbj4YSCsTXs1OFSyjS2T4GXiCYiAHI-TnZNr0zareInbY+PZE5GoubwX6mKKiIH4EGoDDQAD0ACpoIBIc0AnUqAKwYkZ5AOYMgCEGQDRDIBouUAdgyABYZAFcMgHGGQA-DIB2hkA5wyAZ4ZAEkMgBkIwBiDNADXrVNDYb1yJxoFLcDKdknEaTyXSaMrVdENcDQbrDSaLYABCMATbaAaPU7U63V6-UGw5Ho7GYXDE8nNmm5Zmee4aPZHG93B9eYWtcWeqWzebAPiugBc9QAQ5oBT0zrLo9PoDIYjUZjUI7CZV3elUnT8oKwvCNHFxieMnVmu1YP1RrngFgVQCyShuG9vm3ubaHvGZAnqsGxAA)、なぜプロパティじゃなくてデータオブジェクトじゃないといけない？
    - ロジックが散らかるのを防ぐ ?

***値オブジェクト書き換え***
    - [こちら参照](https://www.typescriptlang.org/play?#code/MYGwhgzhAEASCuBbMA7aBvAUNH0AO8ARiAJbDQkAmAXNAJKXa4HFnTED2HlALgJ54AprQBCILrwGCmOFqXKESAJx4ALSmB7DoI5Wo1aZ+IvOgowibQDkL03NGAcUEHkvjAeHJQAoqtF0okKADmADTs4tz8Qv6uQWHseuqa2gAiKeHmlrGBIQCUGEb2aiQQAHRU0AC8ZoIA7vSUvpR5Rbgl5ZxRUtW1DWIS0YLeXZJCrfbFqqVliirJWr0o9TpJBsNz+ikTkzgdZVmCSys2lt6HOzgAvpg3mKCQMAyF9niBAG4p0EqCYJROID40E+IHgdlwjmcrncnh8ILBOXiBSwuxwJAAZtBvABCeGCMrIHjAVTeAD0AD0ANoABgAtABOMC0gBeAEFaQAtAC6ACoACSkvLItq7NRKDgNZYNACiSnFPgA5EEQZUqArLpMbqjoPs8b08UYtbhgoIeN48oiQhhvqb4Eo0LqwKCjjc7g8oDpImMjijmB8vj8-gCgQb7JCAjCvN48ZbgsLtRisdjKQqwArwgrCOnoAqONnU1muRUUKB4JRBBBo06wULrWKJX1oLL5d4lSgVZQIoMpOroEbRdNynqaqHcP3oCazRboAF4tafjw7Q7B2U9a7MPdwB7dPN1i8-SRPotA-8UIDgdXwThw9CPFGY9B0lp46jSaToOJgmQRdA3xRMeadaqOKkorM2UZth2iS7ik6rjlMMzDhezqGkYk7mrQT4+jai72jqK5rrcG7ujApw+kYbyHgGvynueo7Xk4EZ3nCl6xi+uyJlWzplCAgghGo0AAHw1AATNSyL4SBjbgYqypOpUhy9vB7QEZe+qXqh9jodOs5WugOFLvhiFqeuQA)

### 課題3
- ドメインが漏れているとは
    - [こちら参照](https://www.typescriptlang.org/play?ssl=18&ssc=2&pln=1&pc=1#code/MYGwhgzhAECyD2A7CAXApgJ2gbwFDQOgAcBXAIxAEthj4B3TALmkRIFszN9DglUMSwFPAwAKIvSYt2nDAEoc3QoRQALShAB0EhlgC8tXUugBfXGdyhIMAKoQ0AYUhoAjIuUATeKLbMEydHl3ZUJKADNoH21JLAA+aABmAAYFbDNlMwsrKGg7R2cAJmCCLx8-PkDU42VwyLZo3WgAHmgAVhScdMJMoA)
    - ドメインの呼び出し側が、プロパティを使用してロジックをかけてしまう状態。
        - 矛盾したロジックが生まれたり、重複したり、用途が把握しきれなくなるかも
    - https://zenn.dev/praha/articles/92c6494570a4dc


あとでみる
- [DDDにおける値オブジェクトの位置付け(モデルとコード事例あり)[ドメイン駆動設計]](https://little-hands.hatenablog.com/entry/2022/08/15/value-object-in-ddd)
- [CQRSとCQSの違い](https://zenn.dev/praha/articles/4da7c1f91fb91f)