# Optional Class

In Java, the `Optional` class is a container class introduced in Java 8 to represent an optional value, meaning a value that can be either present or absent (null). The purpose of the `Optional` class is to reduce the likelihood of `NullPointerException` and improve code clarity when dealing with potentially null values. It encourages developers to handle null values more explicitly.

Here's how to use the `Optional` class in Java:

1. **Creating an `Optional` instance:**
   You can create an `Optional` instance using the `of`, `ofNullable`, or `empty` methods:

   - `Optional.of(value)`: Creates an `Optional` containing the specified non-null value.
   - `Optional.ofNullable(value)`: Creates an `Optional` containing the specified value, which can be null.
   - `Optional.empty()`: Creates an empty `Optional`.

   ```java
   Optional<String> nonNullOptional = Optional.of("Hello");
   Optional<String> nullableOptional = Optional.ofNullable(null);
   Optional<String> emptyOptional = Optional.empty();
   ```

2. **Accessing the value:**
   You can access the value within an `Optional` using methods like `get`, but it's recommended to use safer alternatives to handle both present and absent values.

   - `get()`: Gets the value if it's present, or throws a `NoSuchElementException` if it's absent.
   - `orElse(defaultValue)`: Returns the value if present, or the specified default value if absent.
   - `orElseGet(supplier)`: Returns the value if present, or uses the supplier function to provide a default value if absent.
   - `orElseThrow(exceptionSupplier)`: Returns the value if present, or throws an exception provided by the exception supplier if absent.

   ```java
   Optional<String> optional = Optional.of("Hello");
   String value = optional.orElse("Default Value");
   ```

3. **Checking if a value is present:**
   You can use methods like `isPresent` to check whether a value is present in the `Optional`.

   ```java
   Optional<String> optional = Optional.ofNullable(null);
   boolean isPresent = optional.isPresent();  // Returns false
   ```

4. **Applying functions with `map`:**
   You can use `map` to apply a function to the value if it's present, and the result will be wrapped in a new `Optional`.

   ```java
   Optional<String> optional = Optional.of("Hello");
   Optional<String> upperCaseOptional = optional.map(String::toUpperCase);
   ```

5. **Filtering with `filter`:**
   You can use `filter` to check a condition on the value within the `Optional` and return a new `Optional` if the condition is met.

   ```java
   Optional<Integer> optional = Optional.of(5);
   Optional<Integer> filteredOptional = optional.filter(val -> val > 0);
   ```

The `Optional` class is a useful tool for making your code more robust and readable when dealing with potentially null values. It encourages you to handle the presence or absence of values explicitly, reducing the chances of unexpected `NullPointerExceptions`.


The `Optional` class in Java provides a set of instance methods that allow you to work with optional values, checking their presence and applying operations when a value is present. Below is a list of some of the most commonly used instance methods of the `Optional` class:

1. **`of(T value)`**:
   - Creates an `Optional` containing the specified non-null value.

2. **`ofNullable(T value)`**:
   - Creates an `Optional` containing the specified value, which can be null.

3. **`empty()`**:
   - Creates an empty `Optional`.

4. **`isPresent()`**:
   - Returns `true` if a value is present in the `Optional`, otherwise returns `false`.

5. **`ifPresent(Consumer<? super T> action)`**:
   - Executes the specified action if a value is present.

6. **`ifPresentOrElse(Consumer<? super T> action, Runnable emptyAction)`**:
   - Executes the specified action if a value is present, or the empty action if no value is present.

7. **`get()`**:
   - Gets the value if it's present. Note that this method should be used with caution to avoid `NoSuchElementException`.

8. **`orElse(T other)`**:
   - Returns the value if present, or the specified default value if absent.

9. **`orElseGet(Supplier<? extends T> other)`**:
   - Returns the value if present, or uses the provided supplier to generate a default value if absent.

10. **`orElseThrow(Supplier<? extends X> exceptionSupplier)`**:
    - Returns the value if present, or throws an exception provided by the exception supplier if absent.

11. **`filter(Predicate<? super T> predicate)`**:
    - Checks a condition on the value within the `Optional` and returns a new `Optional` if the condition is met.

12. **`map(Function<? super T,? extends U> mapper)`**:
    - Applies a function to the value if it's present and returns the result wrapped in a new `Optional`.

13. **`flatMap(Function<? super T,Optional<U>> mapper)`**:
    - Applies a function to the value if it's present and returns the result as an `Optional`. This method is useful when you have an `Optional` of `Optional`.

14. **`equals(Object obj)`**:
    - Compares this `Optional` with another object for equality.

15. **`hashCode()`**:
    - Returns a hash code value for the `Optional`.

16. **`toString()`**:
    - Returns a string representation of the `Optional`, such as "Optional.empty" or "Optional[value]".

These methods allow you to work with optional values safely and effectively, handling both the presence and absence of values. When using `Optional`, it's important to follow best practices to avoid unnecessary complexities in your code.