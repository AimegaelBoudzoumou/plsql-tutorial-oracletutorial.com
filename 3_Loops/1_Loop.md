# LOOP

The PL/SQL LOOP statement is a control structure that repeatedly executes a block of code until a specific condition is met or until you manually exit the loop.

Here’s the syntax of the PL/SQL LOOP statement:
```sql
<<label>>LOOP
  statements
END LOOP loop_label;
```

This structure is the most basic of all the loop constructs including FOR LOOP and WHILE LOOP. This basic LOOP statement consists of a LOOP keyword, a body of executable code, and the END LOOP keywords.

The LOOP statement executes the statements in its body and returns control to the top of the loop. Typically, the body of the loop contains at least one EXIT or EXIT WHEN statement for terminating the loop. Otherwise, the loop becomes an infinite loop.

The LOOP statement can have an optional label that appears at the beginning and the end of the statement.

It is a good practice to use the LOOP statement when:
- You want to execute the loop body at least once.
- You are not sure of the number of times you want the loop to execute.

## EXIT statement

The EXIT statement allows you to unconditionally exit the current iteration of a loop.
```sql
LOOP
  EXIT;
END LOOP;
```

Typically, you use the EXIT statement with an IF statement to terminate a loop when a condition is true:
```sql
LOOP
  IF condition THEN
    EXIT;
  END IF;
END LOOP;
```

The following example illustrates how to use the LOOP statement to execute a sequence of code and EXIT statement to terminate the loop.
```sql
declare
	l_counter NUMBER := 0;
begin
	loop
		l_counter := l_counter + 1;
		if l_counter > 3 then
			exit;
		end if;
		dbms_output.put_line('Inside loop: ' || l_counter);
	end loop;
	dbms_output.put_line('After loop: ' || l_counter);
end;
```

## EXIT WHEN statement
The EXIT WHEN statement has the following syntax:
```sql
EXIT WHEN condition;
```

The EXIT WHEN statement exits the current iteration of a loop when the condition in the WHEN clause is TRUE. Essentially, the EXIT WHEN statement is a combination of an EXIT and an IF THEN statement.

Each time the control reaches the EXIT WHEN statement, the condition is evaluated. If the condition evaluates to TRUE, then the loop terminates. Otherwise, the EXIT WHEN clause does nothing. Inside the loop body, you must make the condition TRUE at some point to prevent an infinite loop.

The following example uses the EXIT WHEN statement to terminate a loop.
```sql
declare
	l_counter NUMBER := 0;
begin
	loop
		l_counter := l_counter + 1;
		EXIT WHEN l_counter > 7;
		dbms_output.put_line('Inside loop: ' || l_counter );
	end loop;
	dbms_output.put_line( 'After loop:' || l_counter);
end;
```
## Constructing nested loops using PL/SQL LOOP statements
It is possible to nest a LOOP statement within another LOOP statement as shown in the following example:

/*
```sql
declare
    l_count_outer NUMBER := 0;
	l_count_inner NUMBER := 0;
begin
    <<outer_loop>>
    loop
    	l_count_outer := l_count_outer + 1;
		EXIT outer_loop WHEN l_count_outer > 2;
		dbms_output.put_line('Outer counter ' || l_count_outer);

		l_count_outer := 0;
			<<inner_loop>>
            l_count_inner := l_count_inner + 1;
			EXIT inner_loop WHEN l_count_inner > 3;
			dbms_output.put_line('Inner counter ' || l_count_inner);
        end loop inner_loop;
    end loop outer_loop;
end;
```
*/

Outer counter 1
 Inner counter 1
 Inner counter 2
 Inner counter 3
Outer counter 2
 Inner counter 1
 Inner counter 2
 Inner counter 3

