# Cursor-based record
A cursor-based record has each field corresponding to a column or alias in the cursor SELECT statement.

To declare a cursor-based record, you use the %ROWTYPE attribute with an explicit cursor as shown below:
```sql
DECLARE
  record_name cursor_name%ROWTYPE;
```

The following example declares a record with the same structure as an explicit cursor:
```sql
DECLARE
  CURSOR c_contacts IS
    SELECT last_name, first_name, phone
    from contacts;

  r_contacts c_contacts%ROWTYPE;
```

In this example:

- First, declare an explicit cursor that fetches data from the first_name, last_name, and phone columns of the contacts table.
- Second, declare a record named r_contact whose structure is the same as the c_contacts cursor.
