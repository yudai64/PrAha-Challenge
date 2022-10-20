```
TABLE Message as m {
  id varchar
  ancestor_id varchar
  text varchar
}


Ref: m.ancestor_id > m.id
```