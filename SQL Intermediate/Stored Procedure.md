# Stored Procedure

A stored procedure is a precompiled and reusable collection of one or more SQL statements and procedural logic, which is stored in a database. It allows you to encapsulate a series of SQL statements into a single unit, which can then be executed with a single call. Stored procedures are used to perform common database operations, such as data manipulation, transaction management, and complex data processing.

Here's an overview of stored procedures and their key characteristics:

1. **Definition:** A stored procedure is created and stored within a database, and it typically has a name, input parameters, and a set of SQL statements.

2. **Parameters:** Stored procedures can take input parameters, allowing you to pass values into the procedure when it's executed. These parameters can be used in SQL statements within the procedure.

3. **Reusability:** Stored procedures are designed for reuse. Once created, they can be called multiple times from different parts of an application or other stored procedures.

4. **Performance:** Stored procedures are precompiled and optimized by the database system, which can improve performance because the execution plan is stored in the database.

5. **Security:** Stored procedures can be used to control access to data. Permissions to execute a stored procedure can be granted or revoked, ensuring that only authorized users can run specific procedures.

6. **Transaction Management:** You can include transaction control statements (BEGIN, COMMIT, ROLLBACK) within stored procedures to ensure data consistency and integrity.

7. **Modularity:** Stored procedures provide a way to modularize code and reduce redundancy by centralizing database-related logic.

Here's a simplified example of creating and using a stored procedure in SQL, using the MySQL syntax:

```sql
-- Create a stored procedure named "GetEmployeeName"
DELIMITER //
CREATE PROCEDURE GetEmployeeName(IN employee_id INT)
BEGIN
  SELECT first_name, last_name FROM employees WHERE employee_id = employee_id;
END;
//
DELIMITER ;

-- Call the stored procedure with an employee ID parameter
CALL GetEmployeeName(123);
```

In this example, we create a stored procedure named "GetEmployeeName" that takes an `employee_id` as an input parameter and retrieves the first name and last name of the employee with that ID. We then call the stored procedure using the `CALL` statement.

Stored procedures are particularly useful in situations where you need to execute complex SQL logic, perform transactions, or enforce data security and integrity within a database. The specific syntax and features of stored procedures may vary between database management systems, so be sure to consult the documentation of your DBMS for details on creating and using stored procedures in your specific system.