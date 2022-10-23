```
TABLE Student {
id varchar
name varchar
status varchar
}

TABLE StudentStatus {
  status varchar
  isActive tinyint
}

ref: Student.status > StudentStatus.status
```