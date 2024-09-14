# Anonymous Block

PL/SQL is a block-structured language whose code is organized into blocks. 

A block consists of three sections:

- Declaration
- Executable
- Exception-handling

In a block, the executable section is mandatory while the declaration and exception-handling sections are optional.

A PL/SQL block has a name. Functions or Procedures is an example of a named block. A named block is stored in the Oracle Database server and can be reusable later.

A block without a name is an anonymous block. An anonymous block is not saved in the Oracle Database server, so it is just for one-time use.

The following picture illustrates the structure of a PL/SQL block:

![image](https://github.com/user-attachments/assets/abf12219-a3bf-45f6-bf76-9dff0cf9d032)

1) __Declaration section__

A PL/SQL block has a declaration section where you declare variables, allocate memory for cursors, and define data types.

3) __Executable section__

A PL/SQL block has an executable section. An executable section starts with the keyword BEGIN and ends with the keyword END. The executable section must have a least one executable statement, even if it is a NULL statement that does nothing.
   
5) __Exception-handling section__

A PL/SQL block has an exception-handling section that starts with the keyword EXCEPTION. The exception-handling section is where you catch and handle exceptions raised by the code in the execution section.

## PL/SQL anonymous block example

```sql
BEGIN
    DBMS_OUTPUT.PUT_LINE('Hello World');
END;
```

It's possible theses two environment to write PL/SQL code :

### 1. SQL*Plus

Some usefull commands on SQL*Plus:
__/__ to execute the preceding bloc
__edit__

### 2.  SQL Developer
- First, connect to the Oracle Database server using Oracle SQL Developer
- Second, create a new SQL file
- Third, enter the PL/SQL code and execute it by clicking the __Execute__ button or pressing the __Ctrl-Enter__ keyboard shortcut.

## More PL/SQL anonymous block examples
```sql
declare
	l_message VARCHAR2( 255 ) := 'Hello World';
begin
	dbms_output.put_line(l_message);
end;
```

The following PL/SQL code catch a __zero divide__ error :
```sql
DECLARE
	v_result NUMBER;
BEGIN
	v_result := 1 / 0;
	EXCEPTION
        WHEN ZERO_DIVIDE THEN
        	DBMS_OUTPUT.PUT_LINE( SQLERRM );
END;
```
Without the above __EXCEPTION__, we get this error :
![image](https://github.com/user-attachments/assets/ce476c04-b5b7-4f36-a593-a15b3de4f61a)

