```
TABLE "ワークスペース" {
  ID varchar
  "ワークスペース名" varchar
}

TABLE "チャネル" {
  ID varchar
  "ワークスペースID" varchar [ref: > "ワークスペース".ID ]
  "チャネル名" varchar
}

TABLE "ユーザー" {
  ID varchar
  "ユーザー名" varchar
}

TABLE "ワークスペース_ユーザー" {
  "ワークスペースID" varchar [ref: > "ワークスペース".ID]
  "ユーザーID" varchar [ref: > "ユーザー".ID]
}

TABLE "チャネル_ユーザー" {
  "チャネルID" varchar [ref: > "チャネル".ID]
  "ユーザーID" varchar [ref: > "ユーザー".ID]
}

TABLE "メッセージ" {
  "ID" varchar
  "ユーザーID" varchar [ref: > "ユーザー".ID]
  "チャネルID" varchar [ref: > "チャネル".ID]
  "メッセージID" varchar [ref: > "メッセージ".ID]
  "本文" varchar
  "作成日時" datetime
}
```