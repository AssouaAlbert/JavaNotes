# Spring Bean Scope

In the Spring Framework, the `@Scope` annotation is used to specify the scope of a Spring bean. The scope defines the lifecycle and visibility of a bean within the Spring IoC container. Different scopes determine how Spring manages the creation and availability of beans. The `@Scope` annotation can be applied to a bean definition method within a `@Configuration` class or to a component class.

Here are some common Spring bean scopes:

1. **Singleton (default)**: This is the default scope. Only one instance of the bean is created, and it's shared across the entire application context. It's created upon application startup and remains in the context until the context is closed.

   ```java
   @Component
   @Scope("singleton")
   public class MySingletonBean {
       // ...
   }
   ```

2. **Prototype**: A new instance of the bean is created whenever it's requested from the Spring container. There can be multiple instances of a prototype bean in the context.

   ```java
   @Component
   @Scope("prototype")
   public class MyPrototypeBean {
       // ...
   }
   ```

3. **Request**: A new instance is created for each HTTP request. This is typically used in web applications.

   ```java
   @Component
   @Scope("request")
   public class MyRequestScopedBean {
       // ...
   }
   ```

4. **Session**: A new instance is created for each user session in a web application. This is used for maintaining user-specific data.

   ```java
   @Component
   @Scope("session")
   public class MySessionScopedBean {
       // ...
   }
   ```

5. **Application**: A single instance is created for the entire web application. This is used for global application-wide state.

   ```java
   @Component
   @Scope("application")
   public class MyApplicationScopedBean {
       // ...
   }
   ```

6. **WebSocket**: A new instance is created for each WebSocket session.

   ```java
   @Component
   @Scope("websocket")
   public class MyWebSocketScopedBean {
       // ...
   }
   ```

7. **Custom Scopes**: You can define custom scopes by implementing the `org.springframework.beans.factory.config.Scope` interface.

   ```java
   @Component
   @Scope("customScope")
   public class MyCustomScopedBean {
       // ...
   }
   ```

It's important to choose the appropriate scope based on the intended behavior of your beans. Singleton is the most common scope, but other scopes are useful in specific situations, especially in web applications.

When using `@Scope` annotation, be sure that you have the necessary infrastructure and context setup to support the chosen scope. For example, using session scope in a non-web application context won't work because there's no concept of an HTTP session.
