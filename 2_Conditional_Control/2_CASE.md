# CASE Statement
The CASE statement chooses one sequence of statements to execute out of many possible sequences.

The CASE statement has two types: simple CASE statement and searched CASE statement. Both types of CASE statements support an optional ELSE clause.

## 1. Simple CASE statement
A simple CASE statement evaluates a single expression and compares the result with some values.

The simple CASE statement has the following structure:
```sql
CASE selector
WHEN selector_value_1 THEN
    statements_1
WHEN selector_value_2 THEN 
    statement_2
...
ELSE
    else_statements
END CASE;
```
If no values in WHEN clauses match the result of the selector in the CASE clause, the sequence of statements in the ELSE clause executes.
Because the ELSE clause is optional, you can skip it. However, if you do so, PL/SQL will implicitly use the following:
```sql
ELSE 
    RAISE CASE_NOT_FOUND;
```

### Simple CASE statement example
The following example compares single value (c_grade) with many possible values ‘A’, ‘B’,’C’,’D’, and ‘F’:
```sql

```


## 2. Searched CASE statement
