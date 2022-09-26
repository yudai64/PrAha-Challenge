Table Manga as m {
  ID int
  name varchar
}

Table MangaComment as mc {
  manga_id int
  comment_id int
}

Table Novel as n {
  ID int
  name varchar
}

Table NovelComment as nc {
  novel_id int
  comment_id int
}

Table Comment as c {
  ID int
  text varchar
}

Ref: mc.manga_id > m.ID
Ref: mc.comment_id > c.ID
Ref: nc.novel_id > n.ID
Ref: nc.comment_id > c.ID