# Workbook 8.3
In this workbook, you will validate fields from incoming request bodies.

## Launch the starter project

![Screen Shot 2022-07-14 at 12.59.39 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fabbcef12-15d1-4a89-b534-6c3badcd244f?alt=media&token=b8d672ba-b9a6-49da-b926-31421e2b871f)


## Task 1 (Review)

Inside `POM.xml`, add the `spring-boot-starter-validation` dependency. It provides the library of files needed to validate fields.

## Task 2 (Review)
Apply validation constraints in the event of a blank name:
```java
    @NotBlank(message = "Name cannot be blank")
```
or a blank phone number:
```java
    @NotBlank(message = "Number cannot be blank")
```

## Task 3
Recall that `@Valid` – based on your constraints – will validate field values that were obtained from the request body. Inside the `RestController`, apply the `@Valid` annotation **where needed**.

## Task 4

In order to handle invalid field arguments, your global exception handler must inherit from `ResponseEntityExceptionHandler`
```java
public class ApplicationExceptionHandler extends ResponseEntityExceptionHandler {
```

Now, **override** the inherited method `handleMethodArgumentNotValid`. Inside the method, access the result of the validation process as follows:

```java
ex.getBindingResult().getAllErrors() //returns list of errors from validation process
```
Just like in section 3, the `BindingResult` carries the result of the validation, and `getAllErrors` returns a `List` of errors from the validation process.

For now, loop through each error inside the errors `List` and print its message.
```java
    for (ObjectError error : ex.getBindingResult().getAllErrors()) {
        System.out.println(error.getDefaultMessage());
    } 

```

Choose an **appropriate** status code from [Mozilla Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses) and return it.
```java
return new ResponseEntity<>(STATUS_CODE_HERE);
```

---

**Test Case:** `POST: localhost:8080/contact`

```json
Request Body
{
    "name": "Tyrion Lannister",
    "phoneNumber": "        "
}
```
**Postman**
![Screen Shot 2022-07-14 at 1.28.17 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F90082fef-dc5c-4700-a3dc-735d8c38e882?alt=media&token=280e8a9b-17b8-4182-937f-190f9efed227)

**Terminal Output:**

`>> Phone number cannot be blank`

## Task 5

Inside `ErrorResponse.java`, convert your `message` field into a List.
```java
    private LocalDateTime timestamp;
    private List<String> message; <--
```
Fix every error inside the `ErrorResponse.java`.
```java
    public ErrorResponse(List<String> message) {
        this.message = message;
        this.timestamp = LocalDateTime.now();
    }
```


Fix the errors inside `handleContactNotFoundException`:
```java
ErrorResponse error = new ErrorResponse(Arrays.asList(ex.getLocalizedMessage()));
```
Inside `handleMethodArgumentNotValid`: 
- Append every error message from the `BindingResult` into a `List<String>`.
- Create an `ErrorResponse` object and return it.
---
**Test Case:** `POST: localhost:8080/contact`

```json
Request Body
{
    "name": "       ",
    "phoneNumber": "        "
}
```
**Response**

![Screen Shot 2022-07-14 at 1.37.12 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F79057349-112b-417e-b99b-b3ae0d7f5c5c?alt=media&token=76c5236b-5486-4796-be90-54b793d64e47)
Spring Boot serializes the `message` `List` into a JSON ARRAY type.

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!