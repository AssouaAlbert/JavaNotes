# Spring Data Annotations

Spring Data provides a set of annotations that can be used to customize the behavior of your repository interfaces, entities, and queries. These annotations help you define specific configurations and behaviors for your data access operations. Here are some of the commonly used Spring Data annotations:

**For Repository Interfaces:**

1. `@Repository`: This annotation is a stereotype annotation for indicating that a class defines a repository. <u>Spring Data repositories are typically interfaces, and this annotation is used to identify them.</u>

2. `@Query`: You can annotate a repository method with `@Query` to specify a custom JPQL (Java Persistence Query Language) query or a native SQL query.

3. `@Param`: Used to specify method parameters when providing custom queries with `@Query`. It helps map method parameters to query parameters in the custom query.

4. `@Procedure`: Used to define a stored procedure execution. It allows you to call stored procedures using Spring Data repositories.

5. `@Modifying`: This annotation is used when you want to execute a query that modifies the database (e.g., an update or delete operation). It informs Spring Data that the query is not read-only.

6. `@EnableJpaRepositories`: Annotation is used in Spring Boot and Spring Data JPA applications to enable and configure Spring Data JPA repositories. It's typically applied to a configuration class that is annotated with @Configuration.

```java
        public interface UserRepository extends JpaRepository<User, Long> {

    // Custom query method to update the email of a user by username
    @Modifying
    @Query("UPDATE User u SET u.email = :newEmail WHERE u.username = :username")
    int updateEmailByUsername(@Param("username") String username, @Param("newEmail") String newEmail);
}
```

6. `@EntityGraph`: Helps define named entity graphs for loading related entities lazily or eagerly. It's often used to optimize fetching strategies in JPA.

7. `@Lock`: Used to specify the locking mode for a query method, which can be applied when executing the query.

**For Entities:**

1. `@Entity`: Marks a class as a JPA entity. It indicates that the class should be managed by JPA and mapped to a database table.

2. `@Id`: Specifies the primary key field of an entity class.

3. `@GeneratedValue`: Indicates that a field is generated (usually an auto-incremented primary key).

4. `@Transient`: Marks a field as non-persistent, meaning it won't be mapped to the database.

**For Query Methods:**

1. `@Query`: You can use `@Query` at the method level to define custom queries for your repository methods. This can be particularly useful when you need to create complex queries.

2. `@Param`: Similar to the `@Param` annotation for repository queries, it helps map method parameters to query parameters in custom queries.

3. `@Procedure`: Marks a method as executing a stored procedure. It is used to call stored procedures using Spring Data repositories.

4. `@Lock`: Specifies the locking mode for a specific query method, overriding the global default specified by `@Lock` in the repository.

These are some of the key Spring Data annotations that you can use to customize and configure your data access logic. The choice of annotations depends on your specific data source (e.g., JPA, MongoDB, Neo4j) and the use cases you want to address. The appropriate annotations may vary for each data source, and they allow you to tailor your data access code to meet your application's requirements.
