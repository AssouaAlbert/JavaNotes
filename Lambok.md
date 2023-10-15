# Lambok
Lombok (pronounced "low-bock") is a Java library that helps reduce boilerplate code in your Java classes by automatically generating common code, such as getters, setters, constructors, toString(), and more, through the use of annotations. Lombok is particularly useful for making your code more concise and maintainable.
Remember that while Lombok annotations can significantly reduce boilerplate code, they also hide some of the code's logic, so use them judiciously and document your code effectively to make it clear to other developers.
Lombok provides a variety of annotations to reduce boilerplate code in your Java classes. While there are many Lombok annotations available, here are some of the most commonly used ones:

0.  `@Getter(lazy=true)`: annotation can be used to create a lazy getter.

1. `@Data`: Generates getters, setters, `equals()`, `hashCode()`, and `toString()` methods for all fields in the class. It's a convenient way to create data objects (POJOs).

2. `@Getter` and `@Setter`: Generate getter and setter methods for fields, respectively. You can use them on individual fields or at the class level.

3. `@NoArgsConstructor`: Generates a no-argument constructor.

4. `@RequiredArgsConstructor`: Generates a constructor that initializes all final fields.

5. `@AllArgsConstructor`: Generates a constructor that initializes all fields.

6. `@ToString`: Generates a `toString()` method that includes all the fields in the class.

7. `@EqualsAndHashCode`: Generates `equals()` and `hashCode()` methods based on the fields of the class.

8. `@Builder`: Generates a builder pattern for your class, allowing for fluent and readable object instantiation.

9. `@Value`: Creates an immutable class by making all fields `final` and generating getters but no setters.

10. `@Accessors`: Customizes the getter and setter naming conventions for fields in the class.

11. `@Slf4j` (or `@Log`, `@CommonsLog`, `@Log4j`, `@Log4j2`, `@XSlf4j`, `@CustomLog`): Generates a logger instance for the class.

12. `@Cleanup`: Automatically closes resources like streams or connections when they go out of scope.

13. `@SneakyThrows`: Suppresses checked exceptions in methods by rethrowing them as unchecked exceptions.

14. `@Synchronized`: Generates synchronized methods to protect access to the annotated methods or blocks.

15. `@NonNull`: Generates null-checks for parameters or fields, and helps document non-null contracts.

16. `@Setter(AccessLevel.NONE)`: Generates setters but sets the access level to private, making fields effectively immutable.

17. `@Wither`: Generates a new instance of the class with modified fields, maintaining immutability.

18. `@Delegate`: Reduces code duplication by delegating method calls to another object.

19. `@Slf4j`: Generates a logger instance for the class using the SLF4J logging framework.

20. `@Cleanup`: Automatically closes resources like streams or connections when they go out of scope.

21. `@SneakyThrows`: Suppresses checked exceptions in methods by rethrowing them as unchecked exceptions.

22. `@Value.Immutable`: Creates an immutable value object with a fluent builder.

23. `@ExtensionMethod`: Allows adding static methods to existing classes.

24. `@DynamicBuilder`: Generates a dynamic builder for fluent object creation.

25. `@ConstructorProperties`: Helps define the names of constructor parameters when generating constructors.

26. `@FieldNameConstants`: Generates constants for field names.

27. `@LogCall`: Automatically logs method calls with entry and exit messages.

28. `@Data(staticConstructor = "of")`: Generates a constructor with a static factory method, often used for value objects.

29. `@ToString.Include`: Specifies which fields to include in the generated `toString()`.

30. `@EqualsAndHashCode.Exclude`: Specifies fields to be excluded from `equals()` and `hashCode()` generation.
