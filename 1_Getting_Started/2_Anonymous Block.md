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

1) Declaration section
   A PL/SQL block has a declaration section where you declare variables, allocate memory for cursors, and define data types.

2) Executable section
   A PL/SQL block has an executable section. An executable section starts with the keyword BEGIN and ends with the keyword END. The executable section must have a least one executable statement, even if it is a NULL statement that does nothing.
   
4) Exception-handling section
   A PL/SQL block has an exception-handling section that starts with the keyword EXCEPTION. The exception-handling section is where you catch and handle exceptions raised by the code in the execution section.
