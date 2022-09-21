Table "リマインダー" as r {
  "ID" int
  "作成者ユーザー" varchar
  "メッセージ" varchar
  "実行頻度" varchar
  "リマインド実行日時" datetime
  "タイムスタンプ" datetime
}

Table "宛先" as u {
  "ID" int
  "リマインダーID" int
  "宛先チャネル" varchar
}

Ref: u."リマインダーID" > r."ID"