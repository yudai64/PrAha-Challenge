### 課題1
#### 外部キー制約を定義しないと起こる問題
- データの整合性が保証されない
  - 存在しないレコードを参照する可能性がある
- テーブル間の関係性を理解するのに時間がかかる
  - 自動ER生成ツールなども利用できない

#### 外部キー制約を定義すると起こる問題
- 親テーブルのデータから作成する必要がある
- シャーディングできない
- パフォーマンスに影響を与える
  - INSERT, UPDATAE, DELETE時に参照整合性を確認するために親テーブルを見に行く必要がある
  - (SELECT 時には有効？)
    - データベース内のテーブル間の関係を把握することで、オプティマイザが最も効率的にクエリを実行するための計画を立てることができる。らしい
  - 親をDELETEする際、参照アクションによっては小テーブルのデータを更新する必要があり、処理に時間がかかる
    - DELETEすることはあまりないかも

### 課題2

|    |  UPDATE  |  DELETE  |
| ---- | ---- | ---- |
|  CASCADE  |  参照先に合わせて更新される  |  削除される  |
|  SET NULL  |  NULL が設定される  |  NULL が設定される  |
|  RESTRICT  |  エラーになる  |  エラーになる  |
|  NO ACTION  |  RESTRICTと同等  |  RESTRICTと同等  |
|  SET DEFAULT  | エラーになる  |  エラーになる  |

`SET DEFAULT` 定義することはできたが期待と違った動きになった

#### 従業員管理サービスの例
- 部署を削除する場合
  - 従業員を別部署に移動させてから削除しないと従業員も削除されてしまう

#### プロジェクトマネジメントツール
- 担当者が削除されてしまった場合、担当者不在の案件が存在してしまう

#### 参照アクションのデフォルト値
- Eloquent (Laravel)
  - RESTRICT
  - DBのデフォルトに合わせて混乱がないようにしている？
- Prisma
  - onUpdateがCascadeなのは一番自然だから？
    - 参照元のIDが変更された場合、それに合わせて更新されるのが一番自然な気がする

|  Clause  |  Optional relations  |  Mandatory relations  |
| ---- | ---- | ---- |
|  onDelete  |  SetNull  |  Restrict  |
|  onUpdate  |  Cascade  |  Cascade  |




#### MySQLとPostgreSQLでの restrictと no action の違い
- MySQL
  - `restrict` = `no action`
    - トランザクション内で参照元をUPDATE/DELETEした時点でエラーになる
- PostgreSQL
  - 失敗するタイミングが違う
    - restrict
      - トランザクション内で参照元をUPDATE/DELETEした時点でエラーになる
    - no action (遅延チェック)
      - トランザクション中で、参照元もUPDATE/DELETEしないとトランザクション失敗する
      - トランザクション内で整合性を取れればOK

### 課題3
- 子テーブルをINSERT時、外部キーを設定している親テーブルはどのような状態になるか。
- 元々単体インデックスが貼られているカラムに対して外部キーを指定した場合、重複してインデックスが貼られる。正しいか。
- 特定のテーブル間のみ外部キー制約を使用するのはありか。

---
### 参考
- [What's wrong with foreign keys?](https://stackoverflow.com/questions/83147/whats-wrong-with-foreign-keys)
- [Thoughts on Foreign Keys? ](https://github.com/github/gh-ost/issues/331)
- [MySQLで外部キー制約を課すべきか](https://ri.hateblo.jp/entry/2017/08/31/115328)
- [外部キー制約が一切ないと何に困るのか？](https://zenn.dev/praha/articles/2667cbb1ab7233)
- [外部キー制約は何も考えずに適用するとよくない](https://blog.j5ik2o.me/entry/2020/06/16/105311)
- [13.1.20.5 FOREIGN KEY の制約](https://dev.mysql.com/doc/refman/8.0/ja/create-table-foreign-keys.html#foreign-key-referential-actions)
- [MySQLの外部キー制約RESTRICT,CASCADE,SET NULL,NO ACTIONの違いは？](https://qiita.com/suin/items/21fe6c5a78c1505b19cb)
- [PostgreSQLアンチパターン：外部キー制約の更新コストを見くびる](https://qiita.com/masudakz/items/ecbfc0f4ace2a7cef0f0)
- [Referential actions](https://www.prisma.io/docs/concepts/components/prisma-schema/relations/referential-actions)
- [MySQL does not support onDelete: setDefault](https://github.com/prisma/prisma/issues/11498)

--- 
テスト用
```
CREATE TABLE parent (
     id INT NOT NULL,
     PRIMARY KEY (id)
) ENGINE=INNODB;

CREATE TABLE child (
     id INT,
     parent_id INT DEFAULT 100,
     INDEX par_ind (parent_id),
     FOREIGN KEY (parent_id)
         REFERENCES parent(id)
         ON UPDATE SET DEFAULT
         ON DELETE SET DEFAULT
) ENGINE=INNODB;
```