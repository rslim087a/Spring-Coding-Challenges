# Workbook 8.2
In workbook 8.1, we handled bad requests by throwing and catching checked exceptions. This method is annoying because it forces you to modify the service methods.

In this workbook, you will handle bad requests using a `ControllerAdvice` class.

## Launch the starter project

![Screen Shot 2022-07-13 at 9.46.09 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F61ddd3d5-0f46-46e7-9228-00672cff0cfc?alt=media&token=02c6d424-ce69-4e37-9d34-11549e8cf82b)

## Task 1

Create a new folder called `exception`. Inside the folder, create a `ContactNotFoundException` class.

Use the following code to create a custom **unchecked** exception:

```java
public class ContactNotFoundException extends RuntimeException { 
    public ContactNotFoundException(String id) { //constructor gets called when exception is thrown
        super("The id '" + id + "' does not exist in our records"); //passing an error message into the parent constructor allows us to access it later...
    }
}
```
## Task 2

Modify the `findIndexById` function to throw the `ContactNotFoundException`.
```java
    private int findIndexById(String id) {
        return IntStream.range(0, contactRepository.getContacts().size())
            .filter(index -> contactRepository.getContacts().get(index).getId().equals(id))
            .findFirst()
            .orElseThrow(() -> new ContactNotFoundException(id));
    }
```
Because it's an unchecked `RuntimeException`, there is no need to catch it. It will just be thrown as the application runs.

## Task 3
Run the application and make a GET request from Postman. There is no data in the ArrayList, so pass in any id.

- `GET: localhost:8080/contact/123`

Because your application threw an exception in the middle of a request, it sends back a 5xx error code. 

![Screen Shot 2022-07-13 at 10.09.05 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F7dd852f1-a19a-464d-9361-2f85fab6f74c?alt=media&token=bc3cedd3-3107-45d8-aca4-e29a912b1db9)

5xx means there was a failure from the server (our application).

![Screen Shot 2022-07-13 at 10.12.52 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F126ff7bb-81bc-4988-aeae-81c6d6b1dd7a?alt=media&token=4bd49d91-f4bf-4c74-ae55-1ee3bc0499e0)

But really, the failure results from the client's bad request. So our application should not fail, it should send back a 4xx error code instead.

---
### New Concept: `@ControllerAdvice`
> class-level annotation that allows you to define global exception handlers.

### New Concept: `@ExceptionHandler`
> method-level annotation that defines an exception handler.

![Screen Shot 2022-07-13 at 11.58.50 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F06f9dfba-89bc-420b-93e2-4d152fac8ff8?alt=media&token=e47896c8-7557-4e5f-b4cd-d57c476c195b)

1. Defines the exception that you want the method to handle.
2. The thrown exception can be accessed from the list of arguments.
---

## Task 4
Create a class called `ApplicationExceptionHandler`. Then apply the `@ControllerAdvice` annotation. By doing so, your class will serve as the global exception handler.

## Task 5

Inside your global exception handler:

- Create a  method called `handleContactNotFoundException`, and mark it as an `@ExceptionHandler`.
- Your exception handler must pick up exceptions of type `ContactNotFoundException`. 
- Your exception handler's return type will be `ResponseEntity<Object>`. This is common practice because `Object` allows us to pass anything into the `ResponseEntity`.
- For now, your method will return a `ResponseEntity` that contains a status code of `404`.



**Test Case:** `GET: localhost:8080/contact/123`

![Screen Shot 2022-07-14 at 12.08.04 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ffa623082-afee-4729-b0f5-5e2a2b1ae3da?alt=media&token=842d160a-7cf2-4f01-b777-0b3186c9838d)

The exception handler handles the exception by responding to the consumer with a 404 status code.

## Task 6

It would be nice to send the user an error response. Inside the `exception` folder, create a class called `ErrorResponse`.

```java
public class ErrorResponse {
    
}
```

Create the following field and generate a complete constructor, getters and setters.
```java
    private String message;
```
## Task 7

Inside `handleContactNotFoundException`, create a new `ErrorResponse` object, and pass the exception's message into the constructor. 
```java
        ErrorResponse errorResponse = new ErrorResponse(ex.getMessage());
```

Return the `errorResponse` object along with the status code.
```java
        return new ResponseEntity<>(errorResponse, HttpStatus.NOT_FOUND);
```
 Spring Boot will automatically serialize the `errorResponse` object inside the `ResponseEntity` into JSON.

**Test Case:** `GET: localhost:8080/contact/123`

![Screen Shot 2022-07-14 at 12.25.38 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F39917490-f009-4889-848d-da5011bc52b5?alt=media&token=ea009a3a-8ae7-4b8d-814f-681ca6cfe6fb)

## Task 8

It would be nice to also send back a timestamp. Add another field inside `ErrorResponse`, and generate the usual getters and setters.
```java
    private LocalDateTime timestamp;
```
Inside the constructor, set the timestamp equal to the current time.
```java
    public ErrorResponse(String message) {
        this.timestamp = LocalDateTime.now();
        this.message = message;
    }
```
**Test Case:** `GET: localhost:8080/contact/123`

![Screen Shot 2022-07-14 at 12.29.53 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F77977372-29b1-46ae-a1f1-a217cc9c91e2?alt=media&token=e13e445c-800c-4306-bc16-73026a43c72e)
The timestamp is barely readable.
## Task 9
You can configure how each property gets serialized into JSON.

![Screen Shot 2022-07-14 at 12.35.31 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fb20a7dd3-d037-41ec-bdb6-3cc8e19f83b7?alt=media&token=4e215a75-947f-4bb4-88b4-40737b503d8c)

1.  Defines the structure to use when serializing into JSON . 
2.  Defines the pattern to use when serializing into JSON.

We wish to configure how the `timestamp` property will be serialized into JSON. The structure we will serialize to will remain JSON `STRING` type. The pattern will be` dd-MM-yyyy hh:mm:ss`
```java
    @JsonFormat(shape = JsonFormat.Shape.STRING, pattern = "dd-MM-yyyy hh:mm:ss")
```
**Test Case:** `GET: localhost:8080/contact/123`

![Screen Shot 2022-07-14 at 12.41.07 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F59ac252a-5563-4620-8320-031e0fe8bad6?alt=media&token=648d42d8-0c56-4f98-a5cb-417e7ed146fa)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!