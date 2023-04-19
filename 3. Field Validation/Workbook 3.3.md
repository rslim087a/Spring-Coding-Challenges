# Workbook 3.3

In this workbook, you will create a custom constraint annotation.

## Task 1

Add the custom `Age` annotation:
- It is applied at the `FIELD` level.
- It is retained at `RUNTIME`.
- It carries a default message of `"INVALID AGE"`;
```java
@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Age {

    String message() default "INVALID AGE";
    Class<?>[] groups() default {};
    Class<? extends Payload>[] payload() default {};

}
```


## Task 2

Apply the annotation on the `dateOfBirth` field, and override the default message.
```html
    @Age(message = "Must be at least 18")
```

## Task 3
As it stands, the annotation isn't connected to any constraint validation logic. Create an `AgeValidator` class, and specify that `Age` is a `@Constraint` that's connected to it.
 
```java
@Constraint(validatedBy =  AgeValidator.class)
```

Inside `AgeValidator.java`, implement the validation logic using the code below. See the cheat sheet if you forgot how to set up a validator.
```java
     long diff = new Date().getTime() - value.getTime();
     int age = (int) (TimeUnit.MILLISECONDS.toDays(diff) / 365);
```

Make the necessary changes inside the HTML to achieve the following output.

-----
![Screen Shot 2022-05-21 at 11.34.42 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc91bec31-f850-408c-91ad-f18f20e0e163?alt=media&token=aff80cfa-c16b-4af9-8b94-695f8a6814ea)


## Task 4
The username cannot contain any special characters ` $ % # @ ^ *` or uppercase letters. Define another annotation named `Username`. Once again, the annotation will be:
- applied at the `FIELD` level.
- retained at `RUNTIME`.
- carry a default message of `"INVALID USERNAME"`;

## Task 5
Apply the annotation on the `username` field, and override the default messsage.
```html
    @Username(message = "Cannot contain special characters or uppercase characters ")
```

## Task 6

Define the annotation as a `@Constraint` that's connected to the `UsernameValidator` class. Use the following code to Implement the validation logic:
```java
    import java.util.regex.Matcher;
    import java.util.regex.Pattern;
                                         
    Pattern pattern = Pattern.compile("[^a-z0-9 ]");
    Matcher matcher = pattern.matcher(value);
    boolean badCharacters = matcher.find(); //false if characters are a-z or 0-9
```

Make the necessary changes to achieve the following output.

### Test Case 1
-----
![Screen Shot 2022-05-22 at 12.41.34 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ff9e60310-cca1-4e1f-b2ef-03a0d3e72fe1?alt=media&token=d656c1ae-d9dd-4b84-a84f-56257f601a0e)

### Test Case 2
-----
![Screen Shot 2022-05-22 at 12.41.45 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F329e3158-efaa-4998-966e-d92a96b27a7d?alt=media&token=7b39e6dc-962f-4809-ba18-0217946a9a9d)


## Task 7
Place the annotation and validator classes in a single folder called `validation`.


--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!