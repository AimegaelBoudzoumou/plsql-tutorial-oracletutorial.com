# Programmer-defined record

## Prerequisite
```sql
create table customers (
    customer_id  integer,
    name         varchar2(100),
    address      varchar2(200),
    website      varchar2(200),
    credit_limit number(10, 2)
);

create table contacts (
    contact_id  integer,
    first_name  varchar2(20),
    last_name   varchar2(20),
    email       varchar2(100),
    phone       integer,
    customer_id integer
);
```

The table-based and cursor-based records are good enough when you need to create records based on existing structures.

If you want to create a record whose structure is not based on the existing ones, then you use a __programmer-defined record__.

To declare a programmer-defined record, you use the following steps:

- Define a record type that contains the structure you want in your record.
- Declare a record based on the record type.

The following shows the syntax for defining a record type:
```sql
TYPE record_type IS RECORD (
  field_name1 data_type1 [[NOT NULL] := | DEFAULT default_value],
  field_name1 data_type1 [[NOT NULL] := | DEFAULT default_value],
  ...
);
```

To declare a record based on the predefined record type, you use the following syntax:
```sql
record_name record_type;
```

The following example defines a record type __r_customer_contact_t__ and a record __r_customer_contact__:
```sql
DECLARE
  -- define a record type
  Type r_customer_contact_t 
  IS 
    RECORD (
      customer_name customers.name%TYPE,
      first_name    contacts.first_name%TYPE,
      last_name     contacts.last_name%TYPE
  );

  -- declare a record
  r_customer_contact r_customer_contact_t; 
    
BEGIN
  NULL;
END;
```

-- cus

