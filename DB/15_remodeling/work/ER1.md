```
// TABLE "決済" {
//   ID varchar
//   "注文ID"  varchar [ref: - "注文".ID]
//   "決済日時" datetime
// }

TABLE "注文" {
  ID varchar
  "注文者名" varchar
  "注文者電話番号" varchar
  "合計金額" integer
  "注文日時" datetime
}

TABLE "注文商品" {
  ID varchar
  "注文ID" varchar [ref: > "注文".ID]
  "メニューID" varchar [ref: > "メニュー".ID]
  "個数" integer
  "わさび有無" varchar
  "サイズID" varchar [ref: > "サイズ".ID]
}

TABLE "サイズ" {
  ID varchar
  "サイズ名" varchar
}

// TABLE "わさび区分" {
//   ID varchar
//   "区分" varchar
// }

TABLE "メニュー" {
  ID varchar
  "商品名" varchar
  "価格" integer
  // "カテゴリーID" varchar [ref: > "カテゴリー".ID]
  // "セットフラグ" boolean
}

TABLE "単品" {
  "ID" varchar
  "メニューID" varchar [ref: - "メニュー".ID]
  // "さび有フラグ" boolean
  // "サイズ" varchar  [ref: - "サイズ".ID]
}

TABLE "セットメニュー" {
  ID varchar
  "メニューID" varchar [ref: - "メニュー".ID]
  "セットカテゴリーID" varchar [ref: - "セットカテゴリー".ID]
}

// TABLE "サイズ" {
//   ID varchar
//   "サイズ名" varchar
// }

TABLE "セット内容" {
  "セットID" varchar [ref: > "セットメニュー".ID]
  "単品ID" varchar [ref: > "単品".ID]
  "個数" integer
}

TABLE "セットカテゴリー" {
  ID varchar
  "カテゴリー名" varchar
}

```