```
TABLE Student {
id varchar
name varchar
status varchar
}

TABLE StudentStatus {
  status varchar
  isActive boolean
}

ref: Student.status > StudentStatus.status
```