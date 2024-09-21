# SELECT INTO

PL/SQL SELECT INTO statement is the simplest and fastest way to fetch a single row from a table into variables. The following illustrates the syntax of the PL/SQL SELECT INTO statement:
```sql
SELECT
  select_list
INTO
  variable_list
FROM
  table_name
WHERE
  condition;
```

In this syntax, the number of columns in the variable_list must be the same as the number of variables (or the number of components of a record) in the select_list.  In addition, their corresponding data type must be compatible.

Besides the WHERE clause, you can use other clauses in the SELECT statement such as INNER JOIN, GROUP BY, HAVING, and UNION.

If the SELECT statement returns more than one row, Oracle will raise the TOO_MANY_ROWS exception. If the SELECT statement does not return any row, Oracle will raise the NO_DATA_FOUND exception.

## PL/SQL SELECT INTO examples
Let’s use these customers and contacts tables for demonstration.

![image](https://github.com/user-attachments/assets/a00dbed1-9208-4543-86a7-abab8906d946)

### 1) Selecting one column example
The following example uses a SELECT INTO statement to get the name of a customer based on the customer id, which is the primary key of the customers table.

```sql
drop table customers;
drop table contacts;

create table customers (
    customer_id  integer,
    name         varchar2(100),
    address      varchar2(200),
    website      varchar2(200),
    credit_limit number(10, 2)
);

create table contacts (
    contact_id  integer,
    first_name  varchar2(20),
    last_name   varchar2(20),
    email       varchar2(100),
    phone       integer,
    customer_id integer
);

insert into customers values (100, 'Massengo', '15 rue Mbiemo - Bifouiti', 'www.plsql-experts.com', 100.50);

DECLARE
  l_customer_name customers.name%TYPE;
BEGIN
  -- get name of customer 100 and assign it to l_customer_name
  SELECT name INTO l_customer_name
  FROM   customers
  WHERE  customer_id = 100;

  -- show the customer name
  dbms_output.put_line ( 'The name is : ' || l_customer_name );
end;
```

### 2) Selecting a complete row example

The following example fetches the entire row from the customers table for a specific customer ID:
```sql
```
