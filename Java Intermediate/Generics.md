# Generics

Generics in Java provide a way to create classes, interfaces, and methods that operate on type parameters. They allow you to write code that is more flexible, reusable, and type-safe by enabling you to work with data structures and algorithms that can work with different types. Generics are especially useful when designing and implementing collections, containers, and algorithms, as they allow you to write code that is not tied to a specific data type.

## Naming Convention for Generics
Technically, type parameters can be named anything you want. The convention is to use single, uppercase letters to make it obvious that they are not real class names.

- E => Element
- K => Map Key
- V => Map Value
- N => Number
- T => Generic data type
- S, U, V, and so on => For multiple generic data types

Key concepts and principles related to generics in Java:

1. **Type Parameter:** A type parameter, represented by angle brackets `<T>`, is a placeholder for a specific data type. For example, `List<T>` represents a generic list that can hold elements of any type.

2. **Generic Classes:** You can create generic classes by specifying type parameters in the class definition. These classes can be instantiated with specific data types.

   ```java
   public class MyGenericClass<T> {
       private T value;

       public MyGenericClass(T value) {
           this.value = value;
       }

       public T getValue() {
           return value;
       }
   }
   ```

3. **Generic Methods:** You can define generic methods within non-generic classes. These methods can have their own type parameters.

   ```java
   public <T> T genericMethod(T input) {
       // Method logic here
       return input;
   }
   ```

4. **Type Bounds:** You can restrict the types that can be used with generics by specifying type bounds. Wildcard types (`?`) can be used for flexibility.

   ```java
   public <T extends Number> double sumOfNumbers(List<T> numbers) {
       // Method logic here
   }
   ```

5. **Wildcards:** Wildcards (`?`) allow you to work with unknown types in a generic class or method.

   - `<?>`: Unbounded wildcard, used for read-only access to generic types.
   - `<? extends T>`: Upper bounded wildcard, restricts the type to a specific superclass of `T`.
   - `<? super T>`: Lower bounded wildcard, accepts `T` and any supertype of `T`.

6. **Type Erasure:** Generics in Java use type erasure, which means that type information is removed at runtime. This helps maintain backward compatibility with older Java code.

7. **Diamond Operator:** The diamond operator (`<>`) allows you to create instances of generic classes without specifying the type arguments on the right side.

   ```java
   List<String> strings = new ArrayList<>();
   ```

8. **Type Safety:** Generics provide compile-time type checking, reducing the likelihood of runtime type errors.

Generics are widely used in Java to create reusable data structures, collections, and algorithms that work with different data types while maintaining type safety. They make Java code more flexible, maintainable, and self-documenting by allowing developers to express the intent of their code in terms of types.
