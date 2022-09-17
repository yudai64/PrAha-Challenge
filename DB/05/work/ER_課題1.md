Table "ユーザー" as u {
  "ID" int
  "ユーザー名" varchar
}

Table "記事" as b {
  "ID" int
  "ユーザーID" int
}

Table "記事履歴" as bh {
  "ID" int
  "記事ID" int
  "タイトル" varchar
  "本文" datetime
  "更新日時" datetime
}

Ref: b."ユーザーID" > u."ID"
Ref: bh."記事ID" > b."ID"