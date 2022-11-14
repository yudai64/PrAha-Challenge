Table Book as b {
  ID int
}

Table Manga as m {
  book_id int
  name varchar
}

Table Novel as n {
  book_id int
  name varchar
}

Table Comment as c {
  book_id int
  text varchar
}

Ref: m.book_id > b.ID
Ref: n.book_id > b.ID
Ref: c.book_id > b.ID