# Spring Data Commons
 Spring Data is a part of the larger Spring ecosystem and provides data access and manipulation support for a variety of data sources, including relational databases, NoSQL databases, and more.

Spring Data Commons provides core functionality and shared interfaces that are used by other Spring Data modules like Spring Data JPA, Spring Data MongoDB, Spring Data Redis, and many others. Some key features and components of Spring Data Commons include:

1. **Repository Interfaces:** Spring Data Commons defines repository interfaces that provide a standard set of CRUD (Create, Read, Update, Delete) operations. These interfaces can be extended to create data repositories for your domain objects.

2. **Query Methods:** Spring Data Commons enables the creation of query methods by simply defining method names in your repository interfaces. The framework translates these method names into appropriate database queries.

3. **Pagination and Sorting:** It offers support for pagination and sorting of query results.

4. **Domain Class Auditing:** Spring Data Commons supports auditing of domain objects, tracking who created and modified records.

5. **Specifications and QueryDSL:** It provides support for creating complex queries using Specifications and QueryDSL.

6. **Type System:** Spring Data Commons defines a type system for working with persistent data types, making it easier to work with data across various data sources.

7. **Custom Implementation:** You can provide custom implementations for repository interfaces if the default CRUD methods are not sufficient for your use case.

8. **Type Information:** It provides a type information system that allows you to work with the data schema of your domain objects.

9. **Projections:** Spring Data Commons supports projections to retrieve only a subset of data from a domain object.

10. **SpEL Expressions:** It allows the use of SpEL (Spring Expression Language) in queries.


## Spring Data Implementations

The following are Spring Data Modules which are specific to the databases.

- Spring Data JPA: Connect to relational databases using ORM frameworks.
- Spring Data MongoDB: Repositories for MongoDB.
- Spring Data REST: Used for RESTful resources around Spring Data repositories.



In practice, Spring Data Commons is typically used in combination with a specific Spring Data module tailored to the data source you're working with (e.g., Spring Data JPA for relational databases, Spring Data MongoDB for MongoDB, etc.). These modules build on the common functionality provided by Spring Data Commons and offer specialized features and support for the respective data sources.

To use Spring Data Commons and a specific Spring Data module, you'll need to include the relevant dependencies in your project and configure your application to use the data source and repositories. The actual configuration and usage may vary depending on the specific Spring Data module you're working with.