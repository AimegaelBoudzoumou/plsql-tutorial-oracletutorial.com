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
insert into contacts values (1235, 'Musseini', 'Jojolana', 'j.museini@gmail.com', 21548512, 100);


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
DECLARE
  r_customer customers%ROWTYPE;
BEGIN
  -- get the information of the customer 100
  SELECT * 
  INTO r_customer
  FROM customers 
  WHERE customer_id = 100;

  -- show the customer info
  DBMS_OUTPUT.PUT_LINE ( r_customer.customer_id || ', ' || 
                         r_customer.name || ', ' || 
                         r_customer.address || ', ' || 
                         r_customer.website || ', ' || 
                         r_customer.credit_limit );
END;
```

### 3) Selecting data into multiple variables example
The following example fetches the names of customers and contacts from the customers and contacts tables for a specific customer id.
```sql

DECLARE
  l_customer_name      customers.name%TYPE;
  l_contact_first_name contacts.first_name%TYPE;
  l_contact_last_name  contacts.last_name%TYPE;

-- other méthod to test :
  -- create a record
  -- CURSOR c_customer_contact IS
    -- SELECT name
  
BEGIN
  -- get customer and contact names
  SELECT name, 
         first_name, 
         last_name
  INTO 
    l_customer_name, 
    l_contact_first_name, 
    l_contact_last_name
  FROM customers cu
  INNER JOIN contacts USING (customer_id)
  WHERE customer_id = 100;

  DBMS_OUTPUT.PUT_LINE( l_customer_name || ' - ' || l_contact_first_name || ' - ' || l_contact_last_name );
END;
```

The following example fetches the names of customers and contacts from the customers and contacts tables for a customers.customer_id match to the contacts.customer_id
Note : le code suivant est à améliorer (piste de réflexion: CURSOR, RECORD)
```sql
insert into customers values (101, 'Mboungou', '1 avenue Matsiona - Mindouli', 'www.plsql-avance.com', 200.90);
insert into customers values (102, 'Ekoka', '89 Bd La Tiémé - Ngamakosso', 'www.plsql-extra.com', 980.90);

insert into contacts values (12458, 'Moussavou', 'Nanatintou', 'nana_la_belle@gmail.com', 254854512, 101);


DECLARE
  l_customer_name      customers.name%TYPE;
  l_contact_first_name contacts.first_name%TYPE;
  l_contact_last_name  contacts.last_name%TYPE;

-- other méthod to test :
  -- create a record
  -- CURSOR c_customer_contact IS
    -- SELECT name
  
BEGIN
  -- get customer and contact names
  SELECT name, 
         first_name, 
         last_name
  INTO 
    l_customer_name, 
    l_contact_first_name, 
    l_contact_last_name
  FROM customers cu
  INNER JOIN contacts co 
  ON cu.customer_id = co.customer_id; 
  --INNER JOIN contacts USING (customer_id)
  --WHERE customer_id = 100;

  DBMS_OUTPUT.PUT_LINE( l_customer_name || ' - ' || l_contact_first_name || ' - ' || l_contact_last_name );
END;
```
Erreur à exploiter :
ORA-06550: line 22, column 9:
PL/SQL: ORA-00918: column ambiguously defined 

## PL/SQL SELECT INTO common errors
