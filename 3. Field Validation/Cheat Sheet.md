# Cheat Sheet

This cheat sheet contains important takeaways from section three.

## Field Validation


| Head | Head |
| --- | --- |
| `@NotBlank` | at least one non-whitespace character
| `@Min` | cannot be less than the minimum |
| `@Max` | cannot exceed the maximum |
| `@NotEmpty` | cannot be null or empty |
| `@Email` | well-formed email address |
| `@Size` | size must be between boundary |
| `@AssertTrue` | must equal `true` |
| `@Past` | is in the past |
| `@Future` | is in the future |

```
@Size(min = 2, message = "Username is too short")
```

- `@Valid`: validates the fields of the object.
- `BindingResult`: carries the result of the validation
- `th:errors`: displays the error message for a violated field.
```java
    @PostMapping(value="path")
    public String postMethodName(@Valid Object object, BindingResult result)
```
**Attention**: You must define the `BindingResult` after `Valid`.

### Custom Constraint Annotation
---
- `@interface`: defines a custom annotation.
- `@Target(FIELD)`: target of your annotation is a field.
- `@Retention(RUNTIME)`: retains annotation during the runtime.
- `@Constraint(validatedBy = Validator.class)`: connects the constraint to a validator.
```java
@Target({ElementType.METHOD, ElementType.FIELD})
@Retention(RetentionPolicy.RUNTIME)
@Constraint(validatedBy = Validator.class)
public @interface AnnotationName {

    //default message if constraint is violated
    String message() default "Invalid Data";
    //boilerplate parameters.
    Class<?>[] groups() default {};
    Class<? extends Payload>[] payload() default {};

}
```
**Validator**: implements the `ConstraintValidator` interface.
```java
public class Validator implements ConstraintValidator<Annotation Type, ValidationType> {
    
    @Override
    public boolean isValid(ValidationType value, ConstraintValidatorContext context) {
        return true OR false;
    }

}
```
Spring Boot uses your definition of `isValid` to validate the custom annotated field.

### Cross-Field Validation
`BindingResult.reject(String field, String errorCode, String errorMessage)`: rejects a field value and adds an error to the `BindingResult`.

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!