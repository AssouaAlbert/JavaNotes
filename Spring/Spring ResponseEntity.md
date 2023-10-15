# Spring ResponseEntity 

`ResponseEntity` is a class in the Spring Framework that represents an HTTP response. It allows you to control the HTTP response status code, headers, and the response body when building responses for your web applications. `ResponseEntity` is often used in Spring MVC controllers, especially when you need more fine-grained control over the response sent to clients.

Key features of `ResponseEntity` include:

1. **HTTP Status Code**: You can set the HTTP status code for the response, indicating the success or failure of the request.

2. **HTTP Headers**: You can specify custom HTTP headers to be included in the response, such as content type, cache control, or custom headers.

3. **Response Body**: You can define the body of the response, which can be any Java object or data structure that can be converted into a response format (e.g., JSON, XML).

Here's how you can use `ResponseEntity` in a Spring MVC controller:

```java
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class MyRestController {

    @GetMapping("/api/greet")
    public ResponseEntity<String> greet() {
        String greeting = "Hello, API!";
        
        HttpHeaders headers = new HttpHeaders();
        headers.add("Custom-Header", "Value");
        
        return ResponseEntity
            .status(HttpStatus.OK)
            .headers(headers)
            .body(greeting);
    }
}
```

In this example:

- We use `ResponseEntity` to specify the response type as `String`.

- We create a `ResponseEntity` object using `ResponseEntity.status(HttpStatus.OK)`, setting the HTTP status code to 200 (OK).

- We add a custom header to the response using `headers.add("Custom-Header", "Value")`.

- We set the response body to a greeting message, "Hello, API!"

Using `ResponseEntity` provides flexibility and control over the response, allowing you to customize the status code, headers, and body according to the specific requirements of your web application or RESTful API. This can be especially useful when you need to return custom responses or handle different error scenarios.

## ResponseEntity offers flexible control of our HTTP Response through several static methods.
- status() method takes in either the int status code or the HttpStatus enum
- body() allows for information & objects to be passed back in the HTTP response body
- header() which takes in two strings for the key-value pair in the HTTP Response headers
- build() for anything that doesn't have a body included with it