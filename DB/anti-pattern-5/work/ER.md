```
TABLE NewCustomer as nc {
  id varchar
}

TABLE CallHistory as ch {
  id varchar
  new_customer_id varchar
  callNote note
  created_at timestamp
}

TABLE InterviewHistory as ih {
  id varchar
  new_customer_id varchar
  metAt date
  created_at timestamp
}

TABLE contract as c {
  id varchar
  new_customer_id varchar
  closedAt date
  created_at timestamp
}

Ref: ch.new_customer_id > nc.id
Ref: ih.new_customer_id > nc.id
Ref: c.new_customer_id > nc.id
```