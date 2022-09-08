Table "リマインダー" as r {
  "ID" int
  "作成者ユーザー" varchar
  "宛先チャネル" varchar
  "メッセージ" varchar
  "頻度ID" int
  "リマインド実行日時" datetime
  "リマインダー作成日時" datetime
}

Table "頻度" as f {
  "ID" int
  "頻度種別" int
  "固有値" int
}

Ref: r."頻度ID" > f."ID"