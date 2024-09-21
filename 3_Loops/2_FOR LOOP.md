# FOR LOOP
PL/SQL FOR LOOP executes a sequence of statements a specified number of times. The PL/SQL FOR LOOP statement has the following structure:
```sql
FOR index IN lower_bound .. upper_bound
LOOP
  statements;
END LOOP;
```

The index is an implicit variable. It is local to the FOR LOOP statement. In other words, you cannot reference it outside the loop.

Inside the loop, you can reference index but you cannot change its value. After the FOR LOOP statement executes, the index becomes undefined.

Both lower_bound and upper_bound are numbers or expressions that evaluate numbers. The lower_bound and upper_bound are evaluated once when the FOR LOOP statement starts. Their values are stored as temporary PLS_INTEGER values. The results of lower_bound and upper_bound are rounded to the nearest integer if necessary.

If lower_bound is equal to upper_bound, the statements execute only once. When lower_bound is greater than upper_bound, the statements do not execute at all.

## PL/SQL FOR LOOP examples

### A) Simple PL/SQL FOR LOOP example
In this example, the loop index is l_counter, lower_bound is one, and upper_bound is five. The loop shows a list of integers from 1 to 5.
```sql
BEGIN
    FOR l_counter IN 1 .. 5
   	LOOP
    	DBMS_OUTPUT.PUT_LINE( l_counter );
	END LOOP;
END;
```

### B) Simulating STEP clause in FOR LOOP statement
The loop index is increased by one after each loop iteration and you cannot change the increment e.g., two, three, and four. However, you can use an additional variable to simulate the increment by two, three, four, etc., as shown in the example below:
```sql
DECLARE
    l_step PLS_INTEGER := 2;
BEGIN
    FOR l_counter IN 1..5 LOOP
    	dbms_output.put_line(l_counter*l_step);
    END LOOP;
END;
```

### C) Referencing variable with the same name as the loop index

```sql
DECLARE
    l_counter PLS_INTEGER := 10;
BEGIN
    FOR l_counter IN  1..5 LOOP
    	dbms_output.put_line(l_counter);
    END LOOP;
	-- after the loop
	DBMS_OUTPUT.PUT_LINE(l_counter);
END;
```
In this example, we had a variable named l_counter, which is also the name of the index. The result shows that l_counter in the FOR loop hides the variable l_counter declared in the enclosing block.

To reference the variable l_counter inside the loop, you must qualify it using a block label as shown below:
```sql
<<outer>>
DECLARE
    l_counter PLS_INTEGER := 10;
BEGIN
    FOR l_counter IN 1..5 loop
    	DBMS_OUTPUT.PUT_LINE('Local counter' || l_counter);
		outer.l_counter := l_counter;
	end loop;
	-- after the loop
	DBMS_OUTPUT.PUT_LINE('Global counter' || l_counter);
END outer;
```

### D) Referencing loop index outside the FOR LOOP
The following example causes an error because it references the loop index, which is undefined, outside the FOR LOOP statement.
```sql
BEGIN
    FOR l_index IN 1..3 LOOP
    	DBMS_OUTPUT.PUT_LINE (l_index);
    END LOOP;
	-- referencing index after the loop
	DBMS_OUTPUT.PUT_LINE (l_index);
END;
```
Oracle issued the following error:
file:///home/chris/Desktop/pls-00201.png![image](https://github.com/user-attachments/assets/4b4d5f36-87b0-48a8-81c6-11811514303e)

## FOR LOOP with REVERSE keyword
The following shows the structure of the FOR LOOP statement with REVERSE keyword:
```sql
FOR index IN REVERSE lower_bound .. upper_bound
LOOP
  statements;
END LOOP;
```

With the REVERSE keyword, the index is set to upper_bound and decreased by one in each loop iteration until it reaches lower_bound.
```sql
BEGIN
    FOR l_counter IN REVERSE 1..3
    LOOP
    	DBMS_OUTPUT.PUT_LINE(l_counter);
    END LOOP;
END;
```
