What is @Transaction
In the context of Spring Framework and Java Persistence Architecture (JPA), `@Transactional` is an annotation used to define the scope of a database transaction. It can be applied to methods or classes, and it instructs Spring to manage the transaction for the annotated method or class.

Key points about the `@Transactional` annotation:

1. **Method-Level Annotation**: When applied to a method, it defines that the method should run within a transaction. This means that the method will be executed as a single unit of work, and any changes made to the database within the method will be either committed or rolled back as a whole.

2. **Class-Level Annotation**: When applied to a class, it defines that all public methods within the class should run within a transaction. This is useful when you want to ensure that all methods within a service or component have the same transactional behavior.

3. **Transaction Management**: The `@Transactional` annotation is used to specify transactional behavior, such as isolation level, propagation behavior, read-only mode, and more. These attributes can be configured in the annotation to control how transactions are managed.

4. **Rollback Rules**: You can specify which exceptions should trigger a rollback of the transaction using the `rollbackFor` attribute. For example, if you specify `@Transactional(rollbackFor = Exception.class)`, any exception of type `Exception` (or its subtypes) will trigger a rollback.

5. **Propagation Behavior**: The `propagation` attribute controls how the method behaves when called from within an existing transaction. Options include `REQUIRED`, `REQUIRES_NEW`, `SUPPORTS`, `MANDATORY`, and others.

6. **Isolation Level**: The `isolation` attribute allows you to specify the isolation level for the transaction, such as `READ_COMMITTED`, `SERIALIZABLE`, etc.

7. **Read-Only Mode**: The `readOnly` attribute can be set to `true` to indicate that the method will only read data and not modify it. This can optimize database performance.

8. **Timeout**: The `timeout` attribute specifies the time (in seconds) that the transaction should wait for a lock before timing out.

Here's an example of using the `@Transactional` annotation:

```java
@Service
public class MyService {
    @Autowired
    private MyRepository repository;

    @Transactional
    public void performTransactionalOperation() {
        // This method runs within a transaction
        repository.save(new Entity());
        // Other database operations
    }
}
```

In this example, the `performTransactionalOperation` method is annotated with `@Transactional`, indicating that it should run within a transaction. Any exceptions thrown within this method will trigger a rollback of the transaction. The specific transactional behavior can be customized by specifying additional attributes in the annotation.

By using `@Transactional`, Spring simplifies the management of database transactions and provides a declarative way to control transactional behavior in your application.




@Transactional (rollbackFor = NegativeWeightException.class , readOnly =  false, isolation = Isolation.READ_COMMITTED, propagation = Propagation.MANDATORY)

The code snippet you provided contains the `@Transactional` annotation, which is commonly used in Spring applications to demarcate transactions. Here's an explanation of the various attributes used in this annotation:

- `rollbackFor = NegativeWeightException.class`: This attribute specifies exceptions for which a rollback should be performed. In this case, if a `NegativeWeightException` or any of its subclasses is thrown during the execution of the method, the transaction will be rolled back. A transaction rollback means that any changes made within the transaction will be discarded.

- `readOnly = false`: This attribute indicates whether the transaction is read-only or not. If `readOnly` is set to `true`, it means that the transaction will only read data and not modify it. Setting it to `false` (as in this case) means that the transaction can read and write data.

- `isolation = Isolation.READ_COMMITTED`: This attribute specifies the transaction isolation level. The `Isolation.READ_COMMITTED` level ensures that the data read within the transaction is committed and visible to other transactions. It prevents dirty reads, non-repeatable reads, and phantom reads.

- `propagation = Propagation.MANDATORY`: This attribute defines the propagation behavior of the transaction. `Propagation.MANDATORY` indicates that the method must run within an existing transaction. If there is no existing transaction, an exception will be thrown. This ensures that the method is part of a larger transaction context and cannot be executed independently.

In summary, the `@Transactional` annotation is used to control transaction behavior in Spring. In the provided code snippet, it specifies that the method should run within a transaction, allowing both read and write operations. It specifies that a rollback should occur if a `NegativeWeightException` is thrown. Additionally, it enforces the `READ_COMMITTED` isolation level and requires the method to run within an existing transaction context.