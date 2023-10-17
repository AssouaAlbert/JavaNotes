# Stream API\

The Stream API in Java is a powerful feature introduced in Java 8 that allows you to process sequences of data in a functional and declarative way. Streams provide a way to perform various operations on data, such as filtering, mapping, reducing, and collecting, without the need for explicit loops. This enables more concise and readable code for working with collections and other data sources. Here's an overview of the key concepts and operations provided by the Stream API:

**Stream Creation:**

1. **From a Collection:**
   You can create a stream from a collection (e.g., List, Set, Map).

   ```java
   List<String> list = Arrays.asList("apple", "banana", "cherry");
   Stream<String> stream = list.stream();
   ```

2. **From Arrays:**
   You can create a stream from an array.

   ```java
   String[] array = {"apple", "banana", "cherry"};
   Stream<String> stream = Arrays.stream(array);
   ```

3. **From Other Sources:**
   You can create streams from various other sources, including I/O, generators, and more.

**Stream Operations:**

Once you have a stream, you can apply various operations to it. These operations are categorized as intermediate and terminal operations:

**Intermediate Operations:**

1. **`filter(Predicate<T> predicate)`:** Filters elements based on the provided condition.
2. **`map(Function<T, R> mapper)`:** Transforms each element using the provided function.
3. **`flatMap(Function<T, Stream<R>> mapper)`:** Maps each element to a stream and flattens the streams into a single stream.
4. **`distinct()`:** Removes duplicate elements.
5. **`sorted()` and `sorted(Comparator<T> comparator)`:** Sorts the elements in natural order or using a provided comparator.
6. **`limit(long maxSize)`:** Limits the number of elements in the stream.
7. **`skip(long n)`:** Skips the first `n` elements in the stream.

**Terminal Operations:**

1. **`forEach(Consumer<T> action)`:** Performs an action on each element in the stream.
2. **`collect(Collector<T, A, R> collector)`:** Collects the stream elements into a result using the provided collector.
3. **`toArray()`:** Converts the stream into an array.
4. **`min(Comparator<T> comparator)` and `max(Comparator<T> comparator)`:** Finds the minimum and maximum elements.
5. **`count()`:** Counts the number of elements in the stream.
6. **`anyMatch(Predicate<T> predicate)`:** Checks if any elements match the given condition.
7. **`allMatch(Predicate<T> predicate)` and `noneMatch(Predicate<T> predicate)`:** Check if all or no elements match the condition.
8. **`reduce(identity, BinaryOperator<T> accumulator)` and `reduce(BinaryOperator<T> accumulator)`:** Combines the elements using an accumulator.
9. **`findFirst()` and `findAny()`:** Returns the first or any element in the stream.
10. **`min()` and `max()`:** Returns the minimum and maximum elements in natural order.

**Lazy Evaluation:**

Streams are evaluated lazily, meaning that intermediate operations are not executed until a terminal operation is invoked. This allows for efficient processing of large data sets.

**Parallel Streams:**

Streams can be processed in parallel using the `parallelStream()` method, which leverages multi-core processors for improved performance.

Here's a simple example of using the Stream API to filter and collect elements from a list:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamExample {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("apple", "banana", "cherry", "date");

        List<String> filteredFruits = fruits.stream()
                .filter(fruit -> fruit.startsWith("a"))
                .collect(Collectors.toList());

        System.out.println(filteredFruits); // Output: [apple]
    }
}
```

In this example, we create a stream from a list of fruits, filter the elements that start with the letter "a," and collect the filtered elements into a new list using the `collect` method.

The Stream API offers a wide range of operations for data processing and manipulation, making it a valuable tool for working with collections and data in a functional and expressive manner.