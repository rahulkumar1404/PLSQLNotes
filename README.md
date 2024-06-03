# PLSQLNotes

* PL/SQL:
-> PL/SQL stands for Procedural Language Extension to SQL.
-> PL/SQL is a block structured language that enables developers to combine the power of SQL with procedural statements.
-> All the statements of a block are passed to oracle engine all at once which increases processing speed and decreases the traffic. 
-> Oracle uses a PL/SQL engine to processes the PL/SQL statements.
-> PL/SQL includes procedural language elements like conditions and loops. 
-> It allows declaration of constants and variables, procedures and functions and triggers.
-> Every PL/SQL statement will be followed by semicolon (;). 
-> PL/SQL blocks can be nested.

Advantages :
1. PL/SQL is a procedural language.
2. PL/SQL is a block structure language. 
3. PL/SQL handles the exceptions. 
4. PL/SQL engine can process the multiple SQL statements simultaneously as a single block 
   hence reduce network traffic and provides better performance.

---------------------------------------------------------------------------------------------------

* Types of PlSQL Blocks:
1) Anonymous Blocks:
Definition: Anonymous blocks are PL/SQL code segments that do not have a name or header.
Purpose: They are used for ad-hoc tasks, quick calculations, or temporary logic.

2) Named Blocks:
Definition: Named blocks have a header (like functions, procedures, or packages).
Purpose: They encapsulate reusable logic and can be called from other PL/SQL code.


------------------------------------------------------------------------------------------------------------------
* PLSQL Building elements:
-> Identifiers are names used to represent various database objects such as variables, constants, procedures, functions, tables, and columns.\
-> Literals are constant values directly specified in the code.
-> The semicolon (;) is used to terminate SQL and PL/SQL statements.In anonymous blocks or named blocks, the semicolon separates statements.
-> Comments provide explanatory notes within the code.
	-> types of comments:
		1) single line comment : it begin with double hyphen(--) and continue until end of line.
		2) multi line comment: it enclosed in /* and */.
----------------------------------------------------------------------------------------------------------------------------

* PLSQL DATATYPES:
1) Scalar Data Types:
-> Scalar data types represent individual values and have no internal components.
 	Examples:
		-> NUMBER: For numeric data (integers, real numbers, etc.).
		-> CHAR, VARCHAR2: For character strings.
		-> BOOLEAN: Represents true or false values.
2) Composite Data Types:
-> Composite data types have internal components that can be manipulated individually.
	Examples:
		-> RECORD: Holds a collection of related fields.
		-> TABLE: Represents a collection of rows.
		-> VARRAY: Variable-size arrays.

3) Reference Data Types:
-> Reference data types hold values (pointers) that designate/points to other items.
	Examples:
		-> REF CURSOR: Used for dynamic queries.
		-> REF TO OBJECT: References to object type

4)LOB(Large Object) data types:
-> It store large objects such as text blocks, images, or videos.
	Examples:
		-> BLOB: Binary large object (for binary data).
		-> CLOB: Character large object (for character data).
		-> NCLOB: National character large object.


--------------------------------------------------------------------------------------------------------------------------------

* Variables in PL/SQL:
-> A variable is a named storage location that holds a value of a specific data type.
-> Variables are declared in the declaration section of a PL/SQL block.
-> Naming conventions:
		-> Prefix with v_ for VARCHAR2.
		-> Prefix with n_ for NUMBER.

------------------------------------------------------------------------------------------------------------------------------------------


* Difference Between Function and Procedure:
                Procedure                             		 Function
1) Procedures are basic PL SQL blocks to perform 		1)Functions are blocks used mainly to perform the computations.
a specific action.
2)Procedures will not return the value				2)Functions must return the value.	
3)Procedures always executes as PL SQL statement		3)Functions can be used as part of an expression (e.g., in SELECT statements).
4)We can pass the values using IN OUT IN OUT parameters`	4)Function must return a single value
5)Procedures can not be executed in Select statement		5)Functions can execute or call using select statement 
										  but it must not contain Out or IN OUT parameters.

--------------------------------------------------------------------------------------------------------------------------------------------

* PROCEDURE:
-> A PL/SQL procedure is a reusable unit of code stored as a schema object in the Oracle Database.
-> It serves as a container for specific business logic, allowing you to modularize your code.
-> Technically, a procedure consists of a header and a body.
-> Procedures enhance code reusability, maintainability, and efficient development practices.

* Procedure Header:
The header specifies the procedure’s name and an optional parameter list.
Parameters can be in three modes:
-> IN: Read-only parameters. You can reference them inside the procedure but cannot modify their values (default mode).
-> OUT: Writable parameters. Typically used for returning values to the calling program.
-> INOUT: Both readable and writable parameters.

syntax:
CREATE [OR REPLACE] PROCEDURE procedure_name
    [ (parameter IN/OUT/IN OUT DATATYPE [,parameter]) ]

IS
    [declaration_section]

BEGIN
    executable_section

[EXCEPTION
    exception_section]

END [procedure_name];

-------------------------------------------------------------------------------------------------------------------------------------------

* FUNCTION:
-> A PL/SQL function is a reusable program unit stored as a schema object in the Oracle Database.
-> It returns a single value, which can be a scalar value (like a number or string) or a record type.
-> Functions can take zero or more parameters and have a specified return type
-> Unlike a procedure, a function must have at least one RETURN statement.
-> PL/SQL functions enhance code reusability and allow you to create modular, efficient logic.

* Function Header:
The function header includes the function name and a RETURN clause that specifies the datatype of the returned value.
Parameters can be in three modes:
IN: Read-only parameters. You can reference them inside the function but cannot modify their values.
OUT: Writable parameters. Typically used for returning values to the calling program.
INOUT: Both readable and writable parameters.

* SYNTAX:
CREATE OR REPLACE FUNCTION function_name (parameter_list) RETURN return_type IS
  [declarative section]
BEGIN
  [executable section]
EXCEPTION
  [exception-handling section]
END;

-----------------------------------------------------------------------------------------------------------------------------------------------

* Package:
-> In PL/SQL, a package is a powerful construct that allows you to organize related code elements into a single unit. 
-> A package is a PL/SQL Object that groups logically related items together.
-> It includes:
		Variables, constants, and types (package data).
		Procedures, functions, and cursors (subprograms).
		Exceptions and other PL/SQL constructs.
-> A package is compiled and stored in the Oracle Database.
-> It acts like a library that can be shared across multiple applications.

* Advantages
-> Modularity and encapsulation
-> Code Reusability
-> Performance Optimization
-> Authorization Management
-> Avoid Unnecessary Recompilation

* Creating a PL/SQL Package:
	A package consists of two parts:
	-> Package Specification: Declares public objects accessible from outside the package (the package’s API).
	-> Package Body: Contains the implementation of the objects declared in the specification.

------------------------------------------------------------------------------------------------------------------------------------------------


* Exception:
-> An exception is an unexpected event that occurs during the execution of a program, disrupting the normal flow of instructions.
-> Exception handling is a mechanism to deal with runtime errors gracefully.
-> PL/SQL provides constructs to catch, handle, and propagate exceptions.
-> Common exceptions include NullPointerException, IOException, SQLException, and

* why used exception ?
-> Preserve the normal flow of the program even when errors occur.
-> Provide meaningful error messages to users.
-> Handle exceptional conditions such as out-of-memory situations or library incompatibility.

* Advantages:
-> Allows you to handle errors gracefully during program execution.
-> Improved Code Robustness
-> Customized error messages help users understand issues.
-> Properly handled exceptions prevent entire transactions from rolling back.
-> Exception handling provides context information for debugging.
-> Avoid silent failure.

* Types of Exception:
 In PL/SQL, there are two main types of exceptions: system-defined exceptions and user-defined exceptions.
	1) System-Defined Exceptions:
	  -> These exceptions are predefined by Oracle and are raised automatically when certain conditions occur.
	  -> They cover common error scenarios and are categorized into named and unnamed exceptions.
	  -> Examples of system-defined exceptions:
			NO_DATA_FOUND: Raised when a SELECT INTO statement returns no rows.
			TOO_MANY_ROWS: Raised when a SELECT INTO statement returns more than one row.
			VALUE_ERROR: Raised for arithmetic, numeric, string, conversion, or constraint errors.
			ZERO_DIVIDE: Raised when dividing by zero.

	2) User-Defined Exceptions:
	  -> These exceptions are defined by the programmer within the PL/SQL code.
	  -> You can create custom exceptions to handle specific application-related errors.
		Examples of user-defined exceptions:
			InvalidInputException: Raised when invalid user input is detected.
			InsufficientFundsException: Raised when an account balance is too low for a transaction.
			CustomBusinessRuleException: Raised for specific business logic violations.


* RAISE_APPLICATION_ERROR 
-> this procedure allows you to issue a user-defined error from a code block or stored program.
-> By using this procedure, you can report errors to the callers instead of returning unhandled exceptions.
-> The error_number is a negative integer with the range from -20999 to -20000.
-> The message is a character string representing the error message (up to 2048 bytes).
-> If the third parameter is FALSE, the error replaces all previous errors. If it is TRUE, the error is added to the stack of previous errors.

------------------------------------------------------------------------------------------------------------------------------------------------------

* Cursor:
-> A cursor is a database object that allows you to retrieve and operate on the result set of a SELECT statement. 
-> types of cursor:
	1)implicit cursor : it automatically creates by sql engine whenever we excute select,insert,update statment.
	2)explicit cursor : -> it creates by programmers.we control cursor cycle with open,fetch,close.
 				  -> explicit cursors provide more control and flexibility when working with query results in PL/SQL


syntax:
cursor cursor_name is select * from table_name;
open cursor_name;
fetch cursor_name into variable_name;
close cursor;


* FOR UPDATE Clause:
-> The FOR UPDATE clause is used in a SELECT statement associated with a cursor.
-> Its purpose is to lock the rows returned by the cursor, preventing other sessions from modifying them until the lock is released.
-> When you open a cursor with a FOR UPDATE clause, all the rows retrieved by the SELECT statement are exclusively locked for your changes.
-> You can extend this clause to lock only specific tables in a multi-table join using the FOR UPDATE OF clause.

* Where current of :
-> The WHERE CURRENT OF clause is used within a cursor’s range for DELETE and UPDATE statements.
-> It simplifies updating or deleting the last fetched row(s) from the cursor.
-> Instead of constructing an UPDATE or DELETE statement with a primary key condition, you can directly use the WHERE CURRENT OF clause.

------------------------------------------------------------------------------------------------------------------------------------                                                     

* REF CURSOR 
-> A REF CURSOR is a named cursor that can be opened and used within a PL/SQL block.
-> Unlike explicit cursors, which are tied to specific queries, a REF CURSOR is more flexible. It is not associated with any particular query.
-> The primary benefit of a REF CURSOR is that it enables passing the result of a query between different PL/SQL programs.
-> Instead of fetching all data from a cursor and storing it in a variable (e.g., a collection), you pass the reference to the cursor itself

types of REF CURSOR:
1)Strong Typed REF CURSOR: Associated with a specific record structure or type.
2)Weak Typed REF CURSOR: Not tied to any specific structure. Starting from Oracle 9i, you can use the predefined SYS_REFCURSOR for weak typed cursors.

----------------------------------------------------------------------------------------------------------------------------------------

* Trigger:
-> A trigger is a procedural code block written in PL/SQL.
-> It automatically executes (or “fires”) when certain predefined events occur, such as INSERT, UPDATE, or DELETE operations on a table.
-> Triggers are stored in the database and can be invoked repeatedly based on the specified triggering events.

* why trigger is important ?
-> Automated Actions: Triggers automate actions in response to events on tables or views.
-> Data Integrity: They help enforce constraints and ensure referential integrity.
-> Consistency: Triggers maintain database consistency by responding immediately to specific events.
-> Error Handling: Triggers handle errors and provide custom error messages.

Types of Trigger:
1)Statement level : it invokes for whole statement once.
2)Row level : it invokes for every row.

syntax:
CREATE OR REPLACE TRIGGER trigger_name
BEFORE | AFTER | INSTEAD OF -- Trigger timing
INSERT | UPDATE | DELETE -- Operation to be performed
OF column_name ON table_name -- Column specification
FOR EACH ROW -- Per row processing
DECLARE
    -- Declaration section
BEGIN
    -- Execution section
EXCEPTION
    -- Exception section
END;

--------------------------------------------------------------------------------------------------------------------------------------

* Compound Trigger:
-> It allows you to specify actions for each of the four timing points within a single trigger body. 
-> These four timing points are:
	-> BEFORE STATEMENT: Executed once before the entire triggering statement (e.g., an INSERT, UPDATE, or DELETE).
	-> BEFORE ROW: Executed before each row affected by the triggering statement.
	-> AFTER ROW: Executed after each row affected by the triggering statement.
	-> AFTER STATEMENT: Executed once after the entire triggering statement completes.

SYNTAX:
CREATE OR REPLACE TRIGGER compound_trigger_name
FOR table_name
COMPOUND TRIGGER
    -- Declarations shared across all timing points
    g_variable NUMBER;

    -- BEFORE STATEMENT timing point
    BEFORE STATEMENT IS
    BEGIN
        -- Initialization code
    END BEFORE STATEMENT;

    -- BEFORE ROW timing point
    BEFORE EACH ROW IS
    BEGIN
        -- Per-row processing
    END BEFORE EACH ROW;

    -- AFTER ROW timing point
    AFTER EACH ROW IS
    BEGIN
        -- Per-row actions
    END AFTER EACH ROW;

    -- AFTER STATEMENT timing point
    AFTER STATEMENT IS
    BEGIN
        -- Finalization code
    END AFTER STATEMENT;
END compound_trigger_name;
/

* Benefits of Compound Triggers
-> Consolidation: Combine multiple triggers into one, reducing complexity.
-> Efficiency: Share global declarations across timing points.
-> Bulk Processing: Accumulate data for bulk operations.
-> Simplicity: Simplify trigger management.

----------------------------------------------------------------------------------------------------------------------------------------

* Collections:
-> In PL/SQL, collections are composite data types that allow you to group related values together. 
-> They provide a way to store multiple elements of the same or different data types. 

* types of collections:
1)Associative Array:
-> Associative Array is composite data types that allow group related values together in the form of set of key-value pair.
-> Each key is unique and is used to locate the corresponding value.
-> The key can be either an integer or a string.
-> also known as index-by-table.
-> associative arrays are unbounded means that they don't have predefined lower and upper limit number of elements.
syntax:
TYPE type_name IS TABLE OF element_type [NOT NULL] INDEX BY subscript_type;  
table_name type_name; -- object declaration
eg. TYPE emp_salary IS TABLE OF NUMBER INDEX BY VARCHAR2(100);
    salary_list emp_salary;
-> first() and next() is useful method used for accessing associative array indexes and manipulating elements effectively.

2)Nested Table:
-> Nested tables are single-dimensional, unbounded collections of homogeneous elements.
-> A nested table is single-dimensional, meaning each row has a single column of data, similar to a one-dimensional array.
-> nested tables are unbounded. This means their size is not predetermined, and you can add or remove elements dynamically.
-> All elements within a nested table must have the same data type.
-> Initially, a nested table is dense, but it can become sparse through the removal of elements.

SYNATX:
TYPE nested_table_type IS TABLE OF element_datatype [NOT NULL];
nested_table_variable.EXTEND; -- TO ADD AN ELEMENT 
nested_table_variable.EXTEND(N); -- TO ADD MULTIPLE ELEMENTS
nested_table_variable(index); TO ACCESS ELEMENT BY INDEX

-> Nested tables have the FIRST and LAST methods that return the first and last indexes of elements respectively.
-> Therefore, you can use these methods to iterate over the elements of a nested table using a FOR loop.

3)VARRAY (VARIABLE-SIZE ARRAY):
-> A VARRAY is single-dimensional collections of elements with the same data type. 
A VARRAY is bounded means that their size is always fixed.
A VARRAY is dense means it does not have gaps between elements(not sparse).

syntax:
TYPE type_name IS VARRAY(max_elements)
    OF element_type [NOT NULL];
varray_name type_name := type_name(element1, element2, ...); -- declare and initilaize
varray_name(n); -- to access element by index

-> the FIRST and LAST methods that return the first and last indexes of elements respectively
-> To delete all elements of a VARRAY, you use the DELETE method.
varray_name.DELETE;
-> To remove one element from the end of a VARRAY, you use the TRIM method.
varray_name.TRIM;
->To remove n elements from the end of a VARRAY, you use the TRIM(n) method.
varray_name.TRIM(n)


---------------------------------------------------------------------------------------------------------------------------

* Record: 
-> A PL/SQL record is a composite data structure that consists of multiple fields.
-> each has its own value. 
PL/SQL has three types of records: 
1) table-based
-> To declare a table-based record, you use the %ROWTYPE attribute with a table name. 
-> A table-based record has each field corresponding to a column in a table.
   record_name table_name%ROWTYPE;

2) cursor-based
-> A cursor-based record has each field corresponding to a column or alias in the cursor SELECT statement.
-> To declare a cursor-based record, you use the %ROWTYPE attribute with an explicit cursor as shown below:
    record_name cursor_name%ROWTYPE;

3)Programmer-defined
-> this created by user as user want.
TYPE record_type IS RECORD (
    field_name1 data_type1 [[NOT NULL] := | DEFAULT default_value],
    field_name2 data_type2 [[NOT NULL] := | DEFAULT default_value],
    ...
);

record_name record_type; ---to declare record variable

---------------------------------------------------------------------------------------------------------------------------

* PLSQL DYNAMIC SQL:
-> Dynamic SQL is a programming methodology for generating and running SQL statements at run time.
-> It is useful when writing general-purpose and flexible programs like ad hoc query systems, 
-> when writing programs that must run database definition language (DDL) statements, or 
-> when you do not know at compile time the full text of a SQL statement or the number or data types of its input and output variables.
-> PL/SQL provides two ways to write dynamic SQL:
	1)Native dynamic SQL, a PL/SQL language (that is, native) feature for building and running dynamic SQL statements
		-> EXECUTE IMMEDIATE statement with the BULK COLLECT INTO clause.
		-> OPEN FOR, FETCH, and CLOSE statements.
	2)DBMS_SQL package, an API for building, running, and describing dynamic SQL statements

* When You Need Dynamic SQL
In PL/SQL, you need dynamic SQL to run:
-> SQL whose text is unknown at compile time.
-> For example, a SELECT statement that includes an identifier that is unknown at compile time (such as a table name) or a 
	WHERE clause in which the number of subclauses is unknown at compile time.
-> SQL that is not supported as static SQL.

* EXECUTE IMMEDIATE Statement
-> The EXECUTE IMMEDIATE statement is the means by which native dynamic SQL processes most dynamic SQL statements.

* if the dynamic SQL statement includes placeholders for bind variables, each placeholder must have a corresponding 
  bind variable in the appropriate clause of the EXECUTE IMMEDIATE statement, as follows:

	-> If the dynamic SQL statement is a SELECT statement that can return at most one row, 
		put out-bind variables (defines) in the INTO clause and in-bind variables in the USING clause.
	
	-> If the dynamic SQL statement is a SELECT statement that can return multiple rows, 
		put out-bind variables (defines) in the BULK COLLECT INTO clause and in-bind variables in the USING clause.


	-> If the dynamic SQL statement is a DML statement without a RETURNING INTO clause, other than SELECT,
		put all bind variables in the USING clause.


	-> If the dynamic SQL statement is a DML statement with a RETURNING INTO clause, 
		put in-bind variables in the USING clause and out-bind variables in the RETURNING INTO clause.

	-> If the dynamic SQL statement is an anonymous PL/SQL block or a CALL statement, 
		put all bind variables in the USING clause.


* OPEN FOR, FETCH, and CLOSE Statements
-> If the dynamic SQL statement represents a SELECT statement that returns multiple rows, 
  you can process it with native dynamic SQL as follows:
	-> Use an OPEN FOR statement to associate a cursor variable with the dynamic SQL statement. In the USING clause of the OPEN FOR statement,
		specify a bind variable for each placeholder in the dynamic SQL statement.

	-> The USING clause cannot contain the literal NULL. To work around this restriction, 
		use an uninitialized variable where you want to use NULL, as in Example 7-7.

	-> Use the FETCH statement to retrieve result set rows one at a time, several at a time, or all at once.

	-> Use the CLOSE statement to close the cursor variable.

* BIND VARIABLE:
-> The most effective way to make your PL/SQL code invulnerable to SQL injection attacks is to use bind variables.
-> The database uses the values of bind variables exclusively and does not interpret their contents in any way. 
-> Bind variables also improve performance.

