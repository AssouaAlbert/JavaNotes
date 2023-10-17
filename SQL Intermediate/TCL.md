# TCL  (**Transaction Control Language**)

SQL TCL (Transaction Control Language) is a subset of SQL (Structured Query Language) used to manage transactions within a relational database. Transactions are sequences of one or more SQL statements that are executed as a single unit of work. SQL TCL statements allow you to control the beginning and ending of transactions, as well as to ensure the integrity of the database in the face of failures or errors. There are four main SQL TCL statements:

1. **COMMIT:** The `COMMIT` statement is used to permanently save the changes made during the current transaction. It essentially ends the transaction and makes all the changes made within it permanent.

   ```sql
   COMMIT;
   ```

2. **ROLLBACK:** The `ROLLBACK` statement is used to undo all the changes made during the current transaction. It is typically used when an error occurs during a transaction, and you want to discard the changes and return the database to its previous state.

   ```sql
   ROLLBACK;
   ```

3. **SAVEPOINT:** The `SAVEPOINT` statement is used to set a point within a transaction to which you can later roll back. This allows for more fine-grained control over which parts of a transaction can be rolled back.

   ```sql
   SAVEPOINT savepoint_name;
   ```

4. **ROLLBACK TO:** The `ROLLBACK TO` statement is used to roll back a transaction to a previously defined savepoint. It undoes all changes made after that savepoint was set.

   ```sql
   ROLLBACK TO savepoint_name;
   ```

Here's an example of how SQL TCL statements can be used in a transaction:

```sql
-- Start a new transaction
BEGIN;

-- Perform some SQL operations (e.g., INSERT, UPDATE, DELETE)
INSERT INTO customers (name, email) VALUES ('John Doe', 'john@example.com');
UPDATE orders SET status = 'Shipped' WHERE order_id = 123;

-- Create a savepoint
SAVEPOINT before_payment;

-- Attempt to process a payment
-- If an error occurs, we can roll back to the savepoint to undo only this part of the transaction
-- For example, if the payment fails, but the other changes should still be saved
-- If successful, commit the transaction
COMMIT;

-- If an error occurred, we can roll back to the savepoint to undo only the payment
-- Otherwise, the changes are permanent
ROLLBACK TO before_payment;
```

TCL statements are essential for ensuring data consistency and reliability when dealing with complex database operations, as they allow you to control and manage transactions effectively.