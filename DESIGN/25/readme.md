### 課題1

#### SOLID原則
***S (Single Responsibility) 単一責任の原則***
- クラスは1つの責任を持つべきというもの。
- 責任が分離されていることで変更箇所や影響範囲が限られる。
- 予期せぬ副作用を防ぐことができる。

***O (Open-Closed) オープン・クローズドの原則***
- ソフトウェアの振る舞いは、既存の成果物を変更せず拡張できるようにするべきである、というもの。
- 既存のコードを壊すリスクを抑えることができる。

***L (Liskov Substitution) リスコフの置換原則***
- サブタイプのオブジェクトはスーパータイプのオブジェクトの仕様に従わなければならない、というもの。
- オープン・クローズドの原則を守るために必要 ?

***I (Interface Segregation) インターフェイス分離の原則***
- インターフェースの実装先が使用しないメソッドへの依存を、強制すべきではない。というもの。
- インターフェースをより小さいものにしようという考え。
- 不要な実装をなくすことができる。またコードの可読性や保守性にもつながる。

***D (Dependency Inversion) 依存性逆転の原則***
- 具体的な実装ではなく、抽象(インターフェースや抽象クラス)に依存すべきである。というもの。
- 疎結合になる。


#### 単一責任の原則と、単純にファイルを細かなファイルに分解することの違い
- 単にファイルを分割するのではなく、同じ責任のものは1クラス(ファイル)にまとめておくべき。

#### Open-Closed-Principleの実例
- [こちら参照](https://www.typescriptlang.org/play?#code/JYOwLgpgTgZghgYwgAgMoAs4AcUG8CwAUMicgOYRgCCUEcAFAJQBcyIArgLYBG0RAvkSIIANnADO45ACUICMHBBkRKYJywrOEcFIzY8RUsiztuI4AmQB3YABMw6Vhx59ipE2YvJ0EYGXRgTly8UEJuJAgA9iDiYFDs8pFQ9Db2jmzB0AA03r7+gRkuUIzIBOFGyA7A4gB0qQ7IALzWdg6GFSRVtT5+AU25vWDtJIKEw+SUNHT9TEFFTQB8peNGtGDsUCCV6NV1rejIAFTbuz3546OjwmKSyADCwFCiquqa2mC6mDjL5R7mllA4LZgOxxHMQmEjFEYnEEmAkvRAcDQeDoCUyh1OjtakiQVJmrjQRdIaQKNRaHAZixCiFFj9Mcg1hstl0aoSpMdWeyjsgAMw1ACMABZiYQroRRBIpFM4Hc4CIEOwxPCoPTkAh5YrlShmvRxF8IGC0AaANoAXWpzlpjSWP3G0NiyDgFP6+v0OIgtgSEHo9CwtByiuKdIxmKZm2MtGQAGp1RsamSZUwLjkAAyMEkkcNbZ10ADc7UuYQdYHVj2eVH6IAgVnu5ZU9AFGYl0UdCHrEAAQlWa3Wng2AEzNkuMuQKJQqSvNau12TyRTKH0CnJD4St0u0ecTrs92djhcN3k5IXD9fqzVKuAq3fIGVyhWXlVrmKRFQ1ESRMj0DUP5VJGo-lqV4+ia7b9hAVCBh2nY5Ju46LpBo5bounYWowQA)
- 新しく図形が追加されたとしても、インターフェースを実装したクラスを作成するだけで済む

#### リスコフの置換原則に違反した場合に起こる不都合
- サブタイプが異なる振る舞いを持っている場合、使用する側で条件分岐が必要な可能性が生じる。(オープン・クローズドの原則に違反することになる)
    - [リスコフの置換原則に違反してはいけない理由](https://qiita.com/yuki153/items/142d0d7a556cab787fad#%E3%83%AA%E3%82%B9%E3%82%B3%E3%83%95%E3%81%AE%E7%BD%AE%E6%8F%9B%E5%8E%9F%E5%89%87%E3%81%AB%E9%81%95%E5%8F%8D%E3%81%97%E3%81%A6%E3%81%AF%E3%81%84%E3%81%91%E3%81%AA%E3%81%84%E7%90%86%E7%94%B1)

#### インターフェースを用いることによる、設計上のメリット
- クラス間が疎結合になる
    - 使い手がインターフェース経由でアクセスしていた場合、クラスの実装に変更があった場合でも使い手の変更が不要になる。
    - テスト容易性も高くなる。
- クラスの機能を保証できる
- クラスへの安全なアクセスを提供できる

#### どんな時に依存性の逆転を用いる必要が生じるか
- 外部システムに依存してしまっているモジュールをテストしたい場合 ?

#### デメテルの法則
> 任意のオブジェクトが自分以外（サブコンポーネント含む）の構造やプロパティに対して持っている仮定を最小限にすべきである

> より形式的に言えば、関数に対するデメテルの法則に従った場合、オブジェクトO上のメソッドMが呼び出してもよいメソッドは以下のオブジェクトに属するメソッドのみに限定される。
> Oそれ自身
> Mの引数に渡されたオブジェクト
> Mの内部でインスタンス化されたオブジェクト
> Oを直接的に構成するオブジェクト（Oのインスタンス変数）

***メリット***
- 違反するような設計の場合、あるモジュールの変更による影響範囲が大きくなってしまう
- 結合度を弱くすることができる

***対応としてgetter, setterを定義する***
- メソッドを知っていることには変わりないので、本質的には変わっていない


### 課題2
- Food for thoughtに記載のあった、性能面以外は思いつかず。。
- 基本的にSQLにはロジックを含まない方が良い派です
    - デバッグとかが手間
    - 複雑になりそうで、理解が困難になりそう

### 課題3
***外部から自由に書き換えられるような状態だと、どのような問題がある？***
- 結合度が高い状態になる ?
- オブジェクトが予期しない状態になった際、いつ、どこで書き換えられたかがデバッグしにくい

***どうすれば解決できる?***
- オブジェクトをイミュータブルにする ?
    - コンストラクタでのみ値を設定できるようにする


---
### 参考
- [SOLID](https://ja.wikipedia.org/wiki/SOLID)
- [イラストで理解するSOLID原則](https://qiita.com/baby-degu/items/d058a62f145235a0f007)
- [SOLID Design Principles Explained: The Single Responsibility Principle](https://stackify.com/solid-design-principles/)
- [【C#】インターフェイスの利点が理解できない人は「インターフェイスには３つのタイプがある」ことを理解しよう](https://qiita.com/yutorisan/items/d28386f168f2f3ab166d)
- [デメテルの法則](https://ja.wikipedia.org/wiki/%E3%83%87%E3%83%A1%E3%83%86%E3%83%AB%E3%81%AE%E6%B3%95%E5%89%87)