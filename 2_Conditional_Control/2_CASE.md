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
DECLARE
    c_grade CHAR( 1 );
	c_rank  VARCHAR2( 20 );
BEGIN
    c_grade := 'Z';
	CASE c_grade
        WHEN 'A' THEN
        	c_rank := 'Excellent';
		WHEN 'B' THEN
            c_rank := 'Very Good';
		WHEN 'C' THEN
            c_rank := 'Good';
		WHEN 'D' THEN
            c_rank := 'Fair';
		WHEN 'E' THEN
            c_rank := 'POOR';
		ELSE
            c_rank := 'No such grade';
	END CASE;
	DBMS_OUTPUT.PUT_LINE( c_rank );
END;
/
```


## 2. Searched CASE statement
The searched CASE statement evaluates multiple Boolean expressions and executes the sequence of statements associated with the first condition that evaluates to TRUE.

The searched CASE statement has the following structure:
```sql
CASE
WHEN condition_1 THEN statements_1
WHEN condition_2 THEN statements_2
...
WHEN condition_n THEN statements_n
[ ELSE
  else_statements ]
END CASE;]
```

The searched CASE statement follows the rules below:

- The conditions in the WHEN clauses are evaluated in order, from top to bottom.
- The sequence of statements associated with the WHEN clause whose condition evaluates to TRUE is executed. If more than one condition evaluates to TRUE, only the first one executes.
- If no condition evaluates to TRUE, the else_statements in the ELSE clause executes. If you skip the ELSE clause and no expressions are TRUE, a CASE_NOT_FOUND exception is raised.

### Searched CASE statement example
The following example illustrates how to use the searched CASE statement to calculate sales commission based on sales revenue.
```sql
DECLARE
    n_sales      NUMBER;
    n_commission NUMBER;
BEGIN
    n_sales := 150000;
	CASE
        WHEN n_sales      > 200000 THEN
        	n_commission := 0.2;
		WHEN n_sales     >= 100000 AND n_sales < 200000 THEN
            n_commission  := 0.15;
		WHEN n_sales     >= 50000 AND n_sales < 100000 THEN
            n_commission := 0.1;
		WHEN n_sales > 30000 THEN
            n_commission := 0.05;
		ELSE
            n_commission := 0;
	END CASE;

	DBMS_OUTPUT.PUT_LINE( 'Commission is ' || n_commission * 100 || '%' ); -- will display : Commission is 15%
END;
/
```
PL/SQL stops evaluating the subsequent condition once it finds the first condition that evaluates to TRUE. Therefore, in this example, PL/SQL will never evaluate the last two conditions in the CASE statement. The ELSE statement clause will also never execute.

### Simple or searched CASE statement
As a rule of thumb, use a searched CASE statement when you want to execute a sequence of statements based on the results of multiple Boolean expressions and use a simple CASE statement when you want to execute a sequence of statements based on the result of a single expression.

## PL/SQL CASE statement vs. CASE expression
PL/SQL also has CASE expression which is similar to the CASE statement.

A CASE expression evaluates a list of conditions and returns one of multiple possible result expressions.

The result of a CASE expression is a single value whereas the result of a CASE statement is the execution of a sequence of statements.

In this tutorial, you have learned how to use the PL/SQL CASE statement to control the flow of a program.
