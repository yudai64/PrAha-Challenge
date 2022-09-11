Table "ユーザー" as u {
  "ID" int
  "ユーザー名" varchar
}

Table "記事" as b {
  "ID" int
  "記事グループID" int
  "ユーザーID" int
  "タイトル" varchar
  "本文" varchar
  "最新フラグ" int
  "更新日時" datetime
  "作成日時" datetime
}

Ref: b."ユーザーID" > u."ID"