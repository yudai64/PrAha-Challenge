```
TABLE Message as m {
  id varchar
  parent_id varchar
  ancestor_id varchar
  text varchar
}


Ref: m.parent_id > m.id
Ref: m.ancestor_id > m.id
```