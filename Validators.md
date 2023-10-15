#What are validators?
In Spring Framework, validators are used to perform data validation on objects, typically in the context of web applications where user input needs to be validated before it is processed. Spring provides a convenient way to perform validation by integrating with JavaBean Validation (JSR-303) and custom validation logic. Here's how you can use validators in Spring:

1. JavaBean Validation (JSR-303):
   Spring supports the JavaBean Validation (JSR-303) specification, which allows you to define validation rules using annotations on your model objects. This is a common and convenient way to perform validation. To use JSR-303 validation in Spring, follow these steps:

   a. Add the necessary dependencies to your project, such as Hibernate Validator.
   b. Annotate your model class fields with validation annotations, such as `@NotNull`, `@Size`, `@Email`, etc.

   Example:
   ```java
   public class User {
       @NotNull
       @Size(min = 3, max = 50)
       private String username;

       @Email
       private String email;
       // ...
   }
   ```

   c. Create a controller or service that uses a Validator to validate the object.

   ```java
   @Controller
   public class UserController {
       @Autowired
       private Validator validator;

       public void validateUser(User user) {
           Set<ConstraintViolation<User>> violations = validator.validate(user);
           // Handle violations (errors) as needed
       }
   }
   ```

2. Custom Validators:
   You can also create custom validators by implementing the `Validator` interface provided by Spring. This approach allows you to define custom validation logic for your objects.

   a. Implement the `Validator` interface and override the `validate` method.

   ```java
   import org.springframework.validation.Errors;
   import org.springframework.validation.ValidationUtils;
   import org.springframework.validation.Validator;

   public class UserValidator implements Validator {
       @Override
       public boolean supports(Class<?> clazz) {
           return User.class.isAssignableFrom(clazz);
       }

       @Override
       public void validate(Object target, Errors errors) {
           User user = (User) target;

           ValidationUtils.rejectIfEmptyOrWhitespace(errors, "username", "field.required");
           if (user.getUsername().length() < 3) {
               errors.rejectValue("username", "field.min.length");
           }
           // Custom validation logic for other fields
       }
   }
   ```

   b. Register your custom validator in the Spring context.

   ```xml
   <bean id="userValidator" class="com.example.UserValidator" />
   ```

   c. Use the validator in your controller or service to validate the object.

   ```java
   @Controller
   public class UserController {
       @Autowired
       private UserValidator userValidator;

       public void validateUser(User user) {
           Errors errors = new BeanPropertyBindingResult(user, "user");
           userValidator.validate(user, errors);
           if (errors.hasErrors()) {
               // Handle validation errors
           }
       }
   }
   ```

These are the two common approaches for using validators in Spring. You can choose the one that best suits your application's requirements and complexity.