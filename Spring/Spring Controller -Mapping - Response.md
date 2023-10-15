# Spring Controller -Mapping - Response

`@Controller`, `@RestController`, `@RequestMapping`, and `@ResponseBody` are annotations in the Spring Framework that are used to create and manage web controllers and handle HTTP requests. They are commonly used in Spring-based web applications to develop RESTful APIs and web services.

Let's explain each of these annotations with examples:

1. **@Controller**:

   - `@Controller` is used to annotate a class as a Spring MVC controller. It indicates that the class is responsible for processing HTTP requests.

   Example:

   ```java
   import org.springframework.stereotype.Controller;
   import org.springframework.web.bind.annotation.RequestMapping;

   @Controller
   public class MyController {
       // Controller methods here
   }
   ```

2. **@RestController**:

   - `@RestController` is a specialization of `@Controller`. It is used to annotate a class as a controller that is primarily responsible for providing RESTful web services. It combines the `@Controller` and `@ResponseBody` annotations.

   Example:

   ```java
   import org.springframework.web.bind.annotation.RestController;
   import org.springframework.web.bind.annotation.RequestMapping;

   @RestController
   public class MyRestController {
       // Controller methods for RESTful services
   }
   ```

3. **@RequestMapping**:

   - `@RequestMapping` is used to map HTTP requests to specific methods within a controller. It allows you to specify the URL path, HTTP method, and other request parameters to map the request to a particular controller method.

   Example:

   ```java
   @RequestMapping("/hello")
   public String hello() {
       return "Hello, World!";
   }
   ```

   Or

   ```java
   import org.springframework.web.bind.annotation.RestController;
   import org.springframework.web.bind.annotation.RequestMapping;

   @RestController
   @RequestMapping("/hello")
   public class MyRestController {
    // Controller methods for RESTful services; GetMapping, PostMappings, etc
   }
   ```

4. **@ResponseBody**:

   - `@ResponseBody` is used in conjunction with a method to indicate that the method's return value should be serialized directly to the HTTP response body, rather than being treated as a view name. This is typically used when you want to return data in a format like JSON or XML.

   Example2:

   ```java
   @RequestMapping("/api/greet")
   @ResponseBody
   public String greet() {
       return "Hello, API!";
   }
   ```

   Or

   ```java
   @RequestMapping("/api/greet")
   public  @ResponseBody String greet() {
       return "Hello, API!";
   }
   ```

In this example, the `greet` method returns a plain string, and the `@ResponseBody` annotation ensures that the string is sent directly as the response body, making it suitable for RESTful services that return simple text or data.

These annotations and their combinations enable you to build web controllers for handling various types of HTTP requests, including traditional web pages (using `@Controller`) and RESTful APIs (using `@RestController`). You can also define request mappings to specify which methods should handle which URLs, and `@ResponseBody` allows you to return structured data directly in the response.
