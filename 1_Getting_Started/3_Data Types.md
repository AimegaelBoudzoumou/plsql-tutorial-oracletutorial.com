# Data Types

Each value in PL/SQL such as a constant, variable and parameter has a data type that determines the storage format, valid values, and allowed operations.

PL/SQL has two kinds of data types: scalar and composite. The scalar types are types that store single values such as number, Boolean, character, and datetime whereas the composite types are types that store multiple values, for example, record and collection.

PL/SQL divides the scalar data types into four families:
- Number
- Boolean
- Character
- Datetime

A scalar data type may have subtypes. A subtype is a data type that is a subset of another data type, which is its base type. A subtype further defines a base type by restricting the value or size of the base data type.

Note that PL/SQL scalar data types include SQL data types and their own data types such as Boolean.

## Numeric data types
The numeric data types represent real numbers, integers, and floating-point numbers. They are stored as NUMBER, IEEE floating-point storage types (BINARY_FLOAT and BINARY_DOUBLE), and PLS_INTEGER.

The data types NUMBER, BINARY_FLOAT, and BINARY_DOUBLE are SQL data types.

The PLS_INTEGER datatype is specific to PL/SQL. It represents signed 32 bits integers that range from -2,147,483,648 to 2,147,483,647.

Because PLS_INTEGER datatype uses hardware arithmetic, they are faster than NUMBER operations, which uses software arithmetic.

In addition, PLS_INTEGER values require less storage than NUMBER. Hence, you should always use PLS_INTEGER values for all calculations in its range to increase the efficiency of programs.

The PLS_INTEGER datatype has the following predefined subtypes: NATURAL, NATURALN, POSITIVE, POSITIVEN, SIGNTYPE, SIMPLE_INTEGER	

Note that PLS_INTEGER and BINARY_INTEGER data types are identical.

## Boolean data type
The BOOLEAN datatype has three data values: TRUE, FALSE, and NULL. Boolean values are typically used in control flow structures such as IF-THEN, CASE, and loop statements like LOOP, FOR LOOP, and WHILE LOOP.

SQL does not have the BOOLEAN data type, therefore, you cannot:
- Assign a BOOLEAN value to a table column.
- Select the value from a table column into a BOOLEAN variable.
- Use a BOOLEAN value in an SQL function.
- Use a BOOLEAN expression in an SQL statement.
- Use a BOOLEAN value in the DBMS_OUTPUT.PUTLINE DBMS_OUTPUT.PUT subprograms.

## Character data types
The character data types represent alphanumeric text. PL/SQL uses the SQL character data types such as CHAR, VARCHAR2, LONG, RAW, LONG RAW, ROWID, and UROWID.

- CHAR(n) is a fixed-length character type whose length is from 1 to 32,767 bytes.
- VARCHAR2(n) is varying length character data from 1 to 32,767 bytes.

## Datetime data types
The datetime data types represent dates, timestamps with or without time zones, and intervals. PL/SQL datetime data types are DATE, TIMESTAMP, TIMESTAMP WITH TIME ZONE, TIMESTAMP WITH LOCAL TIME ZONE, INTERVAL YEAR TO MONTH, and INTERVAL DAY TO SECOND.

## Data type synonyms
Data types have [synonyms](https://www.oracletutorial.com/plsql-tutorial/plsql-data-types/) for compatibility with non-Oracle data sources such as IBM Db2, and SQL Server. It is not a good practice to use data type synonyms unless you are accessing a non-Oracle Database.

