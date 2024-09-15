#  GOTO statement
The GOTO statement allows you to transfer control to a labeled block or statement. The following illustrates the syntax of the GOTO statement:
```sql
GOTO label_name;
```

The __label_name__ is the name of a label that identifies the target statement. In the program, you surround the label name with double enclosing angle brackets as shown below:
```sql
<<label_name>>;
```

When PL/SQL encounters a GOTO statement, it transfers control to the first executable statement after the label.

### GOTO statement example
The following shows an example of using the GOTO statements.
```sql
BEGIN
    GOTO second_message;

	<<first_message>>
    DBMS_OUTPUT.PUT_LINE( 'Hello' );
	GOTO the_end;

	<<second_message>>
    DBMS_OUTPUT.PUT_LINE( 'PL/SQL GOTO Demo' );
	GOTO first_message;

	<<the_end>>
    DBMS_OUTPUT.PUT_LINE( 'and good bye...' );

END;
/
```
![image](https://github.com/user-attachments/assets/4fe82c7a-0a31-4a97-9fa2-098ff00f0d45)

The picture below illustrates the sequence:

![image](https://github.com/user-attachments/assets/3c462ebb-e40c-4797-a87b-a9bd9082b6a7)

## GOTO statement restrictions
The GOTO statement is subject to the following restrictions.

First, you cannot use a GOTO statement to transfer control into an IF, CASE or LOOP statement, the same for the sub-block.

The following example attempts to transfer control into an IF statement using a GOTO statement:
```sql
DECLARE
    n_sales NUMBER;
	n_tax NUMBER;
BEGIN
    GOTO inside_if_statement;
	IF n_sales > 0 THEN
        <<inside_if_statement>>
        n_tax := n_sales * 0.1;
    END IF;
END;
/
```
![image](https://github.com/user-attachments/assets/0668c5fe-d2d5-4060-8596-5984893cffd5)

Second, you cannot use a GOTO statement to transfer control from one clause to another in the IF statement e.g., from IF clause to ELSIF or ELSE clause, or from one WHEN clause to another in the CASE statement.

The following example attempts to transfer control to a clause in the __IF__ statement:
