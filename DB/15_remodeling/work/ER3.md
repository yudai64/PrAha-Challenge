```
TABLE "ユーザー" {
  ID varchar
  "ユーザー名" varchar
}

TABLE "ディレクトリ" {
  ID varchar
  "ディレクトリ名" varchar
  "ルート" boolean
  "ユーザーID" varchar [ref: > "ユーザー".ID]
  "作成日時" datetime
}

TABLE "ディレクトリ_階層" {
  "祖先ID" varchar [ref: - "ディレクトリ".ID]
  "子孫ID" varchar [ref: - "ディレクトリ".ID]
  "深さ" int
}

TABLE "ドキュメント_ソート" {
  "ドキュメントID" varchar [ref: - "ドキュメント".ID]
  "前ドキュメントID" varchar [ref: - "ドキュメント".ID]
  "後ドキュメントリID" varchar [ref: - "ドキュメント".ID]
}

TABLE "ドキュメント" {
  ID varchar
  "ディレクトリID" varchar [ref: > "ディレクトリ".ID]
}

TABLE "最新ドキュメント" {
  "ドキュメント履歴ID" varchar [ref: - "ドキュメント履歴".ID]
  "ドキュメントID" varchar [ref: - "ドキュメント".ID]
}

TABLE "ドキュメント履歴" {
  ID varchar
  "ドキュメントID" varchar [ref: > "ドキュメント".ID]
  "ドキュメント名" varchar
  "本文" varchar
  "更新ユーザーID" varchar [ref: > "ユーザー".ID]
  "更新日時" datetime
}
```