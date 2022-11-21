```
Table "ユーザー" as u {
  "ID" varchar
  "ユーザー名" varchar
}

Table "記事" as b {
  "ID" varchar
  "ユーザーID" int [ref: > "ユーザー".ID]
}

Table "記事履歴" as bh {
  "ID" varchar
  "記事ID" varchar [ref: > "記事".ID]
  "タイトル" varchar
  "本文" datetime
  "更新日時" datetime
}

TABLE "最新記事" {
  "記事ID" varchar [ref: - "記事".ID]
  "記事履歴ID" varchar [ref: - "記事履歴".ID]
}
```