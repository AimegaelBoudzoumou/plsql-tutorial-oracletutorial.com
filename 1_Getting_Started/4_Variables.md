# Variables

In PL/SQL, a variable is named storage location that stores a value of a particular data type. The value of the variable changes through the program. Before using a variable, you must declare it in the declaration section of a block.

## Declaring variables
The syntax for a variable declaration is as follows:
```sql
variable_name datatype [NOT NULL] [:= initial_value];
```

By convention, local variable names should start with __l___ and global variable names should have a prefix of __g___ .

The following example declares three variables l_total_sales, l_credit_limit, and l_contact_name:
```sql
DECLARE
  l_total_sales NUMBER(15,2);
  l_credit_limit NUMBER(10,0);
  l_contact_name VARCHAR2(255);
BEGIN
  NULL;
END;
```

### Default values
PL/SQL allows you to set a default value for a variable at the declaration time. To assign a default value to a variable, you use the assignment operator (:=) or the DEFAULT keyword.

### NOT NULL constraint
If you impose the NOT NULL constraint on a value, then the variable cannot accept a NULL value. Besides, a variable declared with the NOT NULL must be initialized with a non-null value. __Note that PL/SQL treats a zero-length string as a NULL value__.

The following code produce this error : ORA-06502: PL/SQL: numeric or value error ORA-06512: at line 4
```sql
DECLARE
  l_shipping_status VARCHAR2( 25 ) NOT NULL := 'Shipped';
BEGIN
  l_shipping_status := '';
END;
```
Because the variable l_shipping_status declared with the NOT NULL constraint, it could not accept a NULL value or zero-length string in this case.

### Variable assignments
You can assign a value of a variable to another as shown in the following example:
```sql
DECLARE
  l_business_parter VARCHAR2(100) := 'Distributor';
  l_lead_for VARCHAR2(100);
BEGIN
  l_lead_for := l_business_parter;
  DBMS_OUTPUT.PUT_LINE(l_lead_for);
END;
```

### Anchored declarations
PL/SQL allows you to declare a variable whose data type anchor to a table column or another variable. Consider the following example:
```SQL
drop table customers;

create table customers (
  customer_id  integer,
  name         varchar2(100),
  credit_limit number(10,2)
);

insert into customers values (26, 'Massengo', 15.9);
insert into customers values (39, 'Mouloundou', 20.9);

declare
  l_customer_name customers.name%TYPE;
  l_credit_limit  customers.credit_limit%TYPE;
  l_credit_other  l_credit_limit%TYPE; -- l_credit_other  anchors to l_credit_limit
begin
  select
    name, credit_limit, credit_limit
  into
    l_customer_name, l_credit_limit, l_credit_other
  from
    customers
  where
    customer_id = 39;
  dbms_output.put_line(l_customer_name || ':' || l_credit_limit || ' -- ' || l_credit_other);
end;
/
```

Note that : the __l_credit_other__ variable anchors to the variable __l_credit_limit__

