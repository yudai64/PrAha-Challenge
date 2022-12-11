```
TABLE Assignee {
  id varchar
  name varchar
}

TABLE Issue {
  id varchar
  text varchar
  // assigned_to_id varchar
}

TABLE Assignee_Issue {
  assignee_id varchar [ref: > Assignee.id]
  issue_id varchar [ref: > Issue.id]
}
```