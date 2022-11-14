```
TABLE Customer {
  id varchar
}

TABLE Contact {
  customer_id varchar
  status varchar
}

TABLE Called {
  id varchar
  customer_id varchar
  callNote date
  created_at timestamp
}

TABLE Interviewed {
  id varchar
  customer_id varchar
  metAt date
  created_at timestamp
}

TABLE Closed {
  id varchar
  customer_id varchar
  closedAt date
  created_at timestamp
}

TABLE Canceled {
  id varchar
  customer_id varchar
  closedAt date
  created_at timestamp
}

Ref: Contact.customer_id - Customer.id
Ref: Called.customer_id > Customer.id
Ref: Interviewed.customer_id > Customer.id
Ref: Closed.customer_id > Customer.id
Ref: Canceled.customer_id > Customer.id
```