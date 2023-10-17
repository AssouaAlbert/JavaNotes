# Transaction

In SQL, a transaction is a sequence of one or more SQL statements that are executed as a single unit of work. Transactions are used to ensure data integrity and consistency in a relational database. The fundamental properties of a transaction are often referred to as ACID properties, which stand for:

1. **Atomicity:** This property ensures that a transaction is treated as a single, indivisible unit. Either all the changes within the transaction are applied, or none of them are. If any part of the transaction fails, the entire transaction is rolled back, and no changes are made to the database.

2. **Consistency:** A transaction should bring the database from one consistent state to another. The integrity constraints, business rules, and data relationships should be maintained. If a transaction violates any of these constraints, it is rolled back.

3. **Isolation:** This property ensures that transactions are executed in isolation from each other. Even if multiple transactions are being processed simultaneously, the outcome should be as if they were executed one after the other. Isolation prevents one transaction from interfering with or seeing the intermediate state of another. So, while a transaction can see data in the state it was in before another concurrent transaction modified it, as well as after the second transaction has completed, it cannot see any intermediate states.

4. **Durability:** Once a transaction is committed (i.e., its changes are saved to the database), those changes should be permanent and survive any subsequent system failures. The durability property ensures that data remains intact even in the face of crashes, power outages, or other unexpected events. As each transaction is completed, a row is entered in the database transaction log. Thus, in the event of a system failure that requires the database to be restored from a backup you can use this transaction log to get the database back to the state it was in after a successful transaction.

In SQL, you typically work with transactions using the following statements:

1. **BEGIN (or START) TRANSACTION:** This statement marks the beginning of a transaction. All SQL statements that follow will be part of the same transaction until you either `COMMIT` or `ROLLBACK` the transaction.

   ```sql
   BEGIN TRANSACTION;
   -- SQL statements
   ```

2. **COMMIT:** The `COMMIT` statement is used to save all the changes made during the current transaction to the database, making them permanent.

   ```sql
   COMMIT;
   ```

3. **ROLLBACK:** The `ROLLBACK` statement is used to undo all the changes made during the current transaction. It is typically used when an error occurs, and you want to discard the changes and return the database to its previous state.

   ```sql
   ROLLBACK;
   ```

By wrapping a series of SQL statements within a transaction, you can ensure that either all the changes are applied correctly (if the transaction is committed) or none of them are (if the transaction is rolled back), thus maintaining the integrity of the database.