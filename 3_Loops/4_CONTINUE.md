# CONTINUE statement

## PL/SQL CONTINUE statement
The CONTINUE statement allows you to exit the current loop iteration and immediately continue on to the next iteration of that loop.

The CONTINUE statement has a simple syntax:
```sql
CONTINUE;
```

Typically, the CONTINUE statement is used within an IF THEN statement to exit the current loop iteration based on a specified condition as shown below:
```sql
IF condition THEN
  CONTINUE;
END IF;
```

The CONTINUE can be used in all loop constructs including LOOP, FOR LOOP and WHILE LOOP.

### PL/SQL CONTINUE statement example
The following is a simple example of using the CONTINUE statement to skip over loop body execution for odd numbers:
```sql
BEGIN
  FOR n_index IN 1 .. 10
  LOOP
    -- skip odd numbers
    IF MOD(n_index, 2) = 1 THEN
      CONTINUE;
    END IF;
    DBMS_OUTPUT.PUT_LINE(n_index);
  END LOOP;
END;
```

## PL/SQL CONTINUE WHEN statement
The CONTINUE WHEN statement exits the current loop iteration based on a condition and immediately continues to the next iteration of that loop.

The syntax of CONTINUE WHEN statement is:
```sql
CONTINUE WHEN condition;
```

### PL/SQL CONTINUE WHEN statement example

The following example illustrates how to use the CONTINUE WHEN statement to skip over loop body execution for even numbers:
```sql
BEGIN
  FOR n_index IN 1 .. 10
  LOOP
    -- skip even number
    CONTINUE WHEN MOD(n_index, 2) = 0;
    DBMS_OUTPUT.PUT_LINE( n_index );
  END LOOP;
END;
```
