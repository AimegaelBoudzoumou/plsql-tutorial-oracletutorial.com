
# Constants

Unlike a variable, a constant holds a value that does not change throughout the execution of the program.

To declare a constant, you specify the name, CONSTANT keyword, data type, and the default value. The following illustrates the syntax of declaring a constant:
```sql
constant_name CONSTANT datatype [NOT NULL]  := expression
```

## PL/SQL constant examples
The following example declares two constants __co_payment_term__ and __co_payment_status__:
```sql
declare
    co_payment_term   CONSTANT NUMBER  := 45; -- days
	co_payment_status CONSTANT BOOLEAN := FALSE;
begin
    NULL;
end;
/
```

If you attempt to change the co_payment_term in the execution section, PL/SQL will issue an error, for example:
```sql
declare
    co_payment_term   CONSTANT NUMBER  := 45; -- days
	co_payment_status CONSTANT BOOLEAN := FALSE;
begin
    co_payment_term := 30; -- error
end;
/
```
Here is the error message:
![image](https://github.com/user-attachments/assets/f055ccc2-3ad6-43b8-ab07-adb59313c833)

The following illustrates how to declare a constant whose value is derived from an expression:
```sql
DECLARE
    co_pi     CONSTANT REAL := 3.14159;
	co_radius CONSTANT REAL := 10;
	co_area   CONSTANT REAL := (co_pi * co_radius**2);
BEGIN
    DBMS_OUTPUT.PUT_LINE(co_area);
END;
/
```

In this example, the co_area constant receives the value from an expression involving two other constants.
