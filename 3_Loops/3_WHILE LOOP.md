# WHILE Loop
PL/SQL WHILE loop is a control structure that repeatedly executes a code block as long as a specific condition remains true.

Here’s the syntax for the WHILE loop statement:
```sql
WHILE condition
LOOP
  statements;
END LOOP;
```
In this syntax, the condition is a boolean expression that evaluates to TRUE, FALSE or NULL.

The WHILE loop statement continues to execute the statements between the LOOP and END LOOP as long as the condition evaluates to TRUE.

PL/SQL evaluates the condition in the WHILE clause before each loop iteration. If the condition is TRUE, then the loop body executes. If the condition is FALSE or NULL, the loop terminates.

If the condition is FALSE before entering the loop, the WHILE loop does not execute at all. This behavior is different from the LOOP statement whose loop body always executes once.

To terminate the loop prematurely, you use an EXIT or EXIT WHEN statement.

## PL/SQL WHILE loop examples

### 1) Simple PL/SQL WHILE loop example
```sql
DECLARE
  n_counter NUMBER := 1;
BEGIN
  WHILE n_counter <= 5
  LOOP
    dbms_output.put_line('Counter : ' || n_counter);
    n_counter := n_counter + 1;
  END LOOP;
END;
```

### 2) WHILE loop example terminated by EXIT WHEN statement
The following example is the same as the one above except that it has an additional EXITWHEN statement.
```sql
DECLARE
  n_counter NUMBER := 1;
BEGIN
  WHILE n_counter <= 5
  LOOP
    dbms_output.put_line('Counter : ' || n_counter);
    n_counter := n_counter + 1;
    EXIT WHEN n_counter = 3;
  END LOOP;
END;
```
