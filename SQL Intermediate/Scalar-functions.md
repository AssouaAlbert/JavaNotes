# Scalar-functions

Scalar functions, also known as scalar expressions or scalar-valued functions, are a type of SQL function that operates on individual values, typically at the row level, and returns a single result. Unlike aggregate functions, which perform calculations across multiple rows and return a single summary result, scalar functions are applied to each row individually in a result set. Scalar functions are commonly used for data manipulation, transformation, and calculations in SQL queries. Some examples of scalar functions include:

1. **Mathematical Functions:** Scalar functions can perform basic mathematical operations on numeric values, such as addition, subtraction, multiplication, and division. For example:

   ```sql
   SELECT price * 1.1 AS price_with_tax FROM products;
   ```

2. **String Functions:** Scalar functions can manipulate and transform strings, such as concatenation, substring extraction, string length, and case conversion. For example:

   ```sql
   SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;
   ```

3. **Date and Time Functions:** Scalar functions can handle date and time values, allowing you to perform operations like date arithmetic, formatting, and extracting components of date and time values. For example:

   ```sql
   SELECT DATE_ADD(order_date, INTERVAL 7 DAYS) AS future_delivery_date FROM orders;
   ```

4. **Conversion Functions:** Scalar functions can convert data types from one format to another, such as casting strings to numbers or vice versa. For example:

   ```sql
   SELECT CAST('42' AS INT) AS integer_value FROM data;
   ```

5. **Conditional Functions:** Scalar functions can be used for conditional expressions, such as `CASE` statements, which allow you to apply different logic based on certain conditions. For example:

   ```sql
   SELECT CASE WHEN score >= 90 THEN 'A'
               WHEN score >= 80 THEN 'B'
               ELSE 'C' END AS grade FROM students;
   ```

6. **User-Defined Functions:** Some database systems allow you to create your own user-defined scalar functions, which can encapsulate custom logic and calculations. For example, you might create a user-defined function to calculate a customer's age based on their birthdate.

Scalar functions are versatile and allow you to transform and manipulate data within your SQL queries, making them a crucial component of data retrieval and processing. The availability of specific scalar functions may vary depending on the database management system you are using, so it's essential to consult your database's documentation for details on the functions supported by your system.
