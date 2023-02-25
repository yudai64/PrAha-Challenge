### 課題1
#### 図解
![オニオンアーキテクチャ](https://qiita-image-store.s3.amazonaws.com/0/30489/81fcfd95-2ce1-82a8-db69-8618338a5f22.png "オニオンアーキテクチャ")

- 全ての依存関係は円の中心の層に対して向かう。
- システム全体の関心事を分離することを目的としている。
- 保守性の高いアプリケーションにつながる。
- 依存関係逆転の原則によって成り立つ。
- 小規模なWEBサイトには適さず、長寿命のアプリケーションや複雑な動作をするアプリケーションに適している。

(感想)
- ドメインサービスとアプリケーションサービスの違いがいまいちわからない...
    - [What are application and domain services in onion architecture?](https://softwareengineering.stackexchange.com/questions/386554/what-are-application-and-domain-services-in-onion-architecture)
- アプリケーションコアに置くのはインターフェースだけ?
> The first layer around the Domain Model is typically where we would find interfaces that provide object saving and retrieving behavior, called repository interfaces.  The object saving behavior is not in the application core, however, because it typically involves a database.  Only the interface is in the application core.  -- [The Onion Architecture : part 1](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/)

***ドメインモデル***
- ビジネスロジックに関連した状態と振る舞いを一体化したオブジェクトを配置する。
- 他の層への依存関係を持たない。

***ドメインサービス***
- ビジネスロジックに関わる振る舞いのロジック、interfaceなどを配置する。

****アプリケーションサービス***
- アプリケーション固有のロジック、一般的によく利用される制御用のinterafaceなどを配置する。

***インフラ***
- データアクセス、I/O、Webサービスなど
- コモディティであり、アプリケーションに競争上の優位性を与えないコードである

***ユーザインターフェース***
- クライアントと接点を持つ箇所
- ビュー、コントローラーなど

#### ドメインモデル層がどの層にも依存していないことによるメリット
- ライブラリの変更やデータベースの切り替えなどのインフラストラクチャレイヤの変更による影響を受けない。ドメインモデルに変更があった場合のみ、修正することになる。
- ドメインモデルを中心に設計することができる。

#### 層をまたいで依存関係が発生する時（例えばユースケース層がレポジトリ層のメソッドを呼び出す時など）はインターフェースに対する依存のみ許可する。こうすることによるメリットは？

- 疎結合な状態にできる。
- メソッドの実装を変更したい場合、ユースケース層に影響なく変更できる。

#### 「依存性の逆転」がオニオンアーキテクチャにおいてどのように使われているか
- 依存が常に外側の層から内側の層に向かうために、依存性逆転の原則を利用している。
- 内側の層にはインターフェースを配置し、外側の層で実装を行なっている。
- 例えば
    - 従来のレイヤードアーキテクチャではドメイン層がインフラ層に依存している。
    - しかしオニオンアーキテクチャでは、ドメインサービス層にはインターフェースが配置され、実装は外側であるインフラ層に配置される。
    - これにより依存性が逆転し、ドメイン層がインフラ層に依存しない設計になっている。

#### 特定のユーザにしかリソースの追加や更新を許さないようなアクセス制限機能はどの層に記述するのが適切？
- ドメインサービス ?

#### データベースをMySQLからPostgreSQLに変更する場合、どの層を変更する必要があるか

- インフラ ?

### 課題2
- オニオンアーキテクチャの利点はなんでしょうか。
- オニオンアーキテクチャが適するのはどのような場合でしょうか。
- オニオンアーキテクチャが適さないのはどのような場合でしょうか。


---
### 参考
- [オニオンアーキテクチャとは何か](https://qiita.com/cocoa-maemae/items/e3f2eabbe0877c2af8d0)
- [ドメイン駆動設計で実装を始めるのに一番とっつきやすいアーキテクチャは何か[DDD]](https://little-hands.hatenablog.com/entry/2017/10/04/231743)
- [ドメイン駆動 + オニオンアーキテクチャ概略[DDD]](https://little-hands.hatenablog.com/entry/2017/10/11/075634)
- [The Onion Architecture : part 1](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/)
-[Onion Architecture](https://medium.com/expedia-group-tech/onion-architecture-deed8a554423)