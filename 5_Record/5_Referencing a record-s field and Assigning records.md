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
...
```

```
```
