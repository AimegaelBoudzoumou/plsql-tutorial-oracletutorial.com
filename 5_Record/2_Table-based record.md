# Table-based record

To declare a table-based record, you use the %ROWTYPE attribute with a table name. A table-based record has each field corresponding to a column in a table.
```sql
DECLARE
  record_name table_name%ROWTYPE;
```

The following example declares a record named r_contact with the same structure as the contacts table:
```sql
create table contacts (
    contact_id  integer,
    first_name  varchar2(20),
    last_name   varchar2(20),
    email       varchar2(100),
    phone       integer,
    customer_id integer
);
```

```sql
DECLARE
  r_contact contacts%ROWTYPE;
```

