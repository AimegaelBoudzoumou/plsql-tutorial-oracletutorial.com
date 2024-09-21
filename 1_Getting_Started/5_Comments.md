# Comments

PL/SQL comments allow you to describe the purpose of a line or a block of PL/SQL code.

When compiling the PL/SQL code, the Oracle precompiler ignores comments. However, you should always use comments to make your code more readable and to help you and other developers understand it better in the future.

PL/SQL has two comment styles: single-line and multi-line comments.

## Single-line comments
A single-line comment starts with a double hyphen ( --) that can appear anywhere on a line and extend to the end of the line.
```sql
UPDATE products SET list_price = 0; -- WHERE product_id = l_id;
```

## Multi-line comments
A multi-line comment starts with a slash-asterisk ( /* ) and ends with an asterisk slash ( */ ), and can span multiple lines:
```sql
/*
  This is a multi-line comment
  that can span multiple lines
*/
```

Note that it is possible to use a multi-line comment as a single-line comment:
```sql
/* A multi-line comment can be used as a single-line comment */
```

We often use a multi-line comment to describe the purpose of a block of code like the following example:
```sql
/*
    This code allow users to enter the customer id and 
    return the corresponding customer name and credit limit
*/
DECLARE
  l_customer_name customers.name%TYPE;
  l_credit_limit customers.credit_limit%TYPE;
BEGIN
  ...
END;
/
```

For the maintainability, it is not a good practice to mix comments as follows:
```sql
BEGIN
  -- single-line comment /* another comment */
  NULL;
  /*
    multi-line comment 
    -- that has another single-line comment 
  */
END;
/
```

Instead, use the following:
```sql
BEGIN
  -- single-line comment, another comment
  NULL;
  /* 
    multi-line comment 
    that has another single-line comment 
  */
END;
/
```

## PL/SQL comment usage notes
PL/SQL does not allow you to nest a multi-line comment within another multi-line comment. The following code block is not valid:
```sql
BEGIN
    /* 
        a multi-line comment 
        /*
            a nested multi-line comment
        */
    */ -- -> error
END;
/
```

For a PL/SQL block that will be processed dynamically, you cannot use single-line comments. Because Oracle precompiler will ignore the end-of-line characters that cause the single-line comments to extend to the end of the block. In this case, you can use multi-line comments instead.
