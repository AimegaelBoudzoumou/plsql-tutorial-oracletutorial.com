# NULL statement

PL/SQL NULL statement is a statement that does nothing. It serves as a placeholder statement when you need a syntactical construct in your code but don’t want to perform any actual action.

The PL/SQL NULL statement has the following format:
```sql
NULL
```

The NULL statement is a NULL keyword followed by a semicolon ( ;). The NULL statement does nothing except that it passes control to the next statement.

The NULL statement is useful to:
- Improve code readability
- Provide a target for a GOTO statement
- Create placeholders Create placeholders for subprograms

## Using PL/SQL NULL statement to improve code readability
The following code sends an email to employees whose job titles are Sales Representative.
```sql
IF job_title = 'Sales Representatives' THEN
	send_mail;
END IF;
```

What should the program do for employees whose job titles are not Sales Representative? You might assume that it should do nothing. Because this logic is not explicitly mentioned in the code, you may wonder if it misses something else.

To make it more clear, you can add a comment. For example:
```sql
-- Send email to only Sales Representative, 
-- for other employees, do nothing
IF job_title = 'Sales Representatives' THEN
	send_mail;
END IF;
```

Or you can add an ELSE clause that consists of a NULL statement to clearly state that no action is needed for other employees.
```sql
IF job_title = 'Sales Representatives' THEN
	send_mail;
ELSE
    NULL;
END IF;
```

Similarly, you can use a NULL statement in the ELSE clause of a simple CASE statement as shown in the following example:
```sql
DECLARE
    n_credit_status VARCHAR2( 50 );
BEGIN
    n_credit_status := 'GOOD';

	CASE n_credit_status
    WHEN 'BLOCK' THEN
        request_for_aproval; -- must to be declared to execute the pl/sql code
	WHEN 'WARNING' THEN
        send_mail_to_accountant; -- must to be declared to execute the pl/sql code
	ELSE
        NULL;
	END CASE;
END;
```

In this example, if the credit status is not blocked or warning, the program does nothing.

## Using PL/SQL NULL statement to provide a target for a GOTO statement
When using a GOTO statement, you need to specify a label followed by at least one executable statement.

The following example uses a GOTO statement to quickly move to the end of the program if no further processing is required:
```sql
DECLARE
    b_status BOOLEAN;
BEGIN
    IF b_status THEN
    	GOTO end_of_programm;
	END IF;

	<<end_of_programm>>
    NULL;
END;
```

Note that an error will occur if you don’t have the NULL statement after the __end_of_program__ label.

## Creating placeholders for subprograms
The following example creates a procedure named request_for_approval that doesn’t have the code in the body yet. PL/SQL requires at least one executable statement in the body of the procedure in order to compile successfully, therefore, we add a NULL statement to the body as a placeholder. Later you can fill in the real code.
```sql
--DROP PROCEDURE request_for_approval;

CREATE OR REPLACE PROCEDURE request_for_approval(
    custumer_id           NUMBER,
    customer_presentation VARCHAR2
)
AS
BEGIN
    NULL;
END;
```
