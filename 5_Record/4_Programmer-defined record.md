# Programmer-defined record

The table-based and cursor-based records are good enough when you need to create records based on existing structures.

If you want to create a record whose structure is not based on the existing ones, then you use a __programmer-defined record__.

To declare a programmer-defined record, you use the following steps:

- Define a record type that contains the structure you want in your record.
- Declare a record based on the record type.

The following shows the syntax for defining a record type:
```sql
TYPE record_type IS RECORD (
  fied
)

