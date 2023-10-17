# Aggregate-functions

SQL aggregate functions are special functions that perform a calculation on a set of values and return a single value. These functions are commonly used in SQL queries to summarize or derive information from data in a database. Some of the most frequently used aggregate functions in SQL include:

1. **COUNT:** The `COUNT` function counts the number of rows in a result set, or the number of non-null values in a specific column.

   ```sql
   SELECT COUNT(*) FROM orders;
   SELECT COUNT(DISTINCT column_name) FROM table_name;
   ```

2. **SUM:** The `SUM` function calculates the sum of numeric values in a column.

   ```sql
   SELECT SUM(total_price) FROM sales;
   ```

3. **AVG:** The `AVG` function calculates the average of numeric values in a column.

   ```sql
   SELECT AVG(salary) FROM employees;
   ```

4. **MAX:** The `MAX` function returns the maximum value in a column.

   ```sql
   SELECT MAX(score) FROM students;
   ```

5. **MIN:** The `MIN` function returns the minimum value in a column.

   ```sql
   SELECT MIN(price) FROM products;
   ```

6. **GROUP_CONCAT or STRING_AGG (depending on the RDBMS):** These functions concatenate values from multiple rows into a single string, often separated by a specified delimiter.

   ```sql
   SELECT GROUP_CONCAT(product_name SEPARATOR ', ') FROM products;
   -- In SQL Server:
   SELECT STRING_AGG(product_name, ', ') FROM products;
   ```

7. **STDEV and VARIANCE:** These functions are used for statistical calculations. `STDEV` calculates the sample standard deviation, and `VARIANCE` computes the sample variance of values in a column.

   ```sql
   SELECT STDEV(sales_amount) FROM sales_data;
   SELECT VARIANCE(salary) FROM employee_data;
   ```

8. **FIRST and LAST (depending on the RDBMS):** These functions return the first and last values in a sorted result set, respectively.

   ```sql
   -- In PostgreSQL:
   SELECT FIRST_VALUE(product_name) FROM products ORDER BY price;
   SELECT LAST_VALUE(product_name) FROM products ORDER BY price;
   ```

9. **DISTINCT:** While not a traditional aggregate function, `DISTINCT` is used to retrieve unique values from a column.

   ```sql
   SELECT DISTINCT category FROM products;
   ```

10. **HAVING:** The `HAVING` clause is used with the `GROUP BY` clause to filter the results of aggregate functions based on a condition.

   ```sql
   SELECT department, AVG(salary) as avg_salary
   FROM employees
   GROUP BY department
   HAVING AVG(salary) > 50000;
   ```

Aggregate functions are valuable for summarizing and analyzing data in a database, and they are often used in conjunction with the `GROUP BY` clause to perform calculations on groups of data within a result set. The specific functions available and their syntax may vary slightly between different database management systems (e.g., MySQL, PostgreSQL, SQL Server), so it's important to consult the documentation for your particular RDBMS for precise details.