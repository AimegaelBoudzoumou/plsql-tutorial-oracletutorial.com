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
Consider the following exampe:
```sql
DECLARE
    b_profitable BOOLEAN;
	n_sales      NUMBER;
    n_costs      NUMBER;
BEGIN
    b_profitable := false;
	IF n_sales > n_costs THEN
        b_profitable := true;
    END IF;
END;
/
```

In this example, the __IF__ statement determines whether the sales revenue is higher than the cost and updates the __b_profitable__ variable accordingly.

This __IF__ statement called a clumsy __IF__ statement because you can assign the result of a Boolean expression directly to a Boolean variable as follows:
```sql
b_profitable := n_sales > n_costs;
```

### Tip #2: Avoid evaluating Boolean variables
A Boolean variable is always TRUE, FALSE, or NULL. Therefore the following comparison is unnecessary:
```sql
IF b_profitable = TRUE THEN
	DBMS_OUTPUT.PUT_LINE( 'This sales deal is profitable' );
END IF;
```

Instead, use:
```sql
IF b_profitable THEN
	DBMS_OUTPUT.PUT_LINE( 'This sales deal is profitable' );
END IF;
```

## 2. IF THEN ELSE statement
Syntax:
```sql
IF condition THEN
    statement;
ELSE
    else_statements;
END IF;
```

### IF THEN ELSE statement example
The following example sets the sales commission to 10% if the sales revenue is greater than 200,000. Otherwise, the sales commission is set to 5%.
```sql
/*
The following example sets the sales commission to 10% if the sales revenue is greater than 200,000. 
Otherwise, the sales commission is set to 5%.
*/

DECLARE
    n_sales      NUMBER := 1000;
	n_commission NUMBER( 10, 2) := 0;
BEGIN
    IF n_sales > 200000 THEN
    	n_commission := n_sales * 0.1;
    ELSE
        n_commission := n_sales * 0.05;
    END IF;
	DBMS_OUTPUT.PUT_LINE('Commission = ' || n_commission); -- will display : Commission = 50
END;
/
```
## 3. IF THEN ELSIF statement
The following illustrates the structure of the IF THEN ELSIF statement:
```sql
IF condition_1 THEN
  statements_1
ELSIF condition_2 THEN
  statements_2
[ ELSIF condition_3 THEN
    statements_3
]
...
[ ELSE
    else_statements
]
END IF;
```

In this structure, the condition between IF and THEN, which is the first condition, is always evaluated. Each other condition between ELSEIF and THEN is evaluated only if the preceding condition is FALSE. For example, the condition_2 is evaluated only if the condition_1 is false, the condition_3 is evaluated only if the condition_2 is false, and so on.

If a condition is true, other subsequent conditions are not evaluated. If no condition is true, the else_statements between the ELSE and ENDIF execute. In case you skip the ELSE clause and no condition is TRUE, then the IF THEN ELSIF does nothing

### IF THEN ELSIF statement example
```sql
DECLARE
    n_sales NUMBER := 300000;
	n_commission NUMBER( 10, 2 ) := 0;
BEGIN
    IF n_sales > 200000 THEN
    	n_commission := n_sales * 0.1;
	ELSIF n_sales <= 20000 AND n_sales > 100000 THEN
        n_commission := n_sales * 0.05;
	ELSIF n_sales <= 100000 AND n_sales > 50000 THEN
        n_commission := n_sales * 0.03;
	ELSE
        n_commission := n_sales * 0.02;
	END IF;
END;
/
```

## Nested IF statement
You can nest an IF statement within another IF statement as shown below:
```sql
IF condition_1 THEN
    IF condition_2 THEN
        nested_if_statements;
    END IF;
ELSE
    else_statements;
END IF; 

```
However, if you have too many levels of nesting, the code will be hard to read and maintain, so you should avoid nesting the IF statements.
