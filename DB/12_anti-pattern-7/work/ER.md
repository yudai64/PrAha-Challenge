```
TABLE Student {
  student_id varchar
}

TABLE taikaiEvent {
  id varchar
  student_id varchar [ref: > Student.student_id]
  created_at timestamp
}

TAbLE ActiveStudent {
  student_id varchar [ref: - Student.student_id]
  name varchar
}

TABLE TaikaiStudent {
  student_id varchar [ref: - Student.student_id]
  name varchar
}
```