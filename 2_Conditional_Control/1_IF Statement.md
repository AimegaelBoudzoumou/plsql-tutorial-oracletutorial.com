# IF Statement

The IF statement allows you to either execute or skip a sequence of statements, depending on a condition. 

The IF statement has three forms:

__IF THEN__

__IF THEN ELSE__

__IF THEN ELSIF__

## 1. IF THEN statement
Syntax :
```sql
IF condition THEN
    statements;
END IF;
```
The condition is a Boolean expression that always evaluates to TRUE, FALSE, or NULL.

If the condition evaluates to TRUE, the statements after the THEN execute. Otherwise, the IF statement does nothing.

### IF THEN statement example
```sql
DECLARE n_sales NUMBER := 2000000;
BEGIN
    IF n_sales > 1000000 THEN
    	DBMS_OUTPUT.PUT_LINE( 'Sales revenue is greater than 100K' );
	END IF;
END;
/
```

### Tip # 1: Avoid clumsy IF statement
