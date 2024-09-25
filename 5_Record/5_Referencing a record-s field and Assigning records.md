# Referencing a record’s field
You reference a field in a record via the dot notation as shown below:
```sql
record_name.field_name;
```

For example, to reference the first_name field of the r_contact record, you use the following expression:
```sql
r_contact.first_name;
```

# Assigning records
You can assign a record to another record of the same type, for example:
```sql
r_contact1 := r_contact2;
```

But you cannot compare two records of the same type via a comparison operator. The following example is an invalid comparison:
```sql
IF r_contact1 = r_contact2 THEN
  ...
END IF;
```

In this case, you need to compare individual fields of the record instead:
```sql
IF r_contact1.first_name = r_contact2.first_name AND
   r_contact1.last_name  = r_contact2.last_name AND
   r_contact1.phone      = r_contact2.phone     THEN
    ...
END IF;
```
You can assign a value to the individual field of a record, for example:
```sql
r_contact1.first_name := 'Jonh';
r_contact1.last_name  := 'Doe';
r_contact1.phone := '(251-512-0265)';
```

You can use SELECT INTO a whole record (or individual fields):
```sql
DROP TABLE contacts;

CREATE TABLE contacts (
    contact_id integer,
    first_name varchar2(100),
    last_name  varchar2(100),
    phone      varchar2(100)
);

insert into contacts values (100,'Paul', 'Museni', '521-584-5412');

DECLARE
  r_contact contacts%ROWTYPE;
BEGIN
  SELECT
    contact_id, first_name, last_name, phone
  INTO
    r_contact
  FROM
    contacts
  WHERE
    contact_id = 100;
END;
```

You can FETCH INTO a whole record or individual fields:
```SQL
-- fetch a whole record
FETCH cur_contacts INTO r_contact;

-- fetch individual fields
FETCH
  cur_contacts
INTO
  r_contact.first_name,
  r_contact.last_name,
  r_contact.phone;
```

Example
```sql

```
