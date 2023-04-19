# Cheat Sheet

This cheat sheet contains important takeaways that lead up to section eight.

## REST API

### Definitions
- `API`: Mediator between a consumer and a system
- `REST API`: API that conforms to a set of guidelines.
- `JSON`: universal format of key-value pairs that all systems can understand. 
```json
{
    "name": "Tyrion Lannister",  //JSON STRING
    "phoneNumber": "4515429321",  // JSON STRING
    "age": 40,  // JSON NUMBER
    "height": 1.2,  // JSON NUMBER
    "siblings": [ "Cersei", "Jaime" ], // JSON ARRAY
    "alwaysDrunk": true // JSON BOOLEAN
}
```

### REST Guidelines:

- **Resource**: piece of data that can be named (Contact, Employee).
- **URI**: Uniform Resource Identifier – identifies the location of  a resource.
- The API defines operations that can manipulate resources:
    - GET: retrieves a resource.
    - POST: creates a resource.
    - PUT: updates a resource.
    - DELETE: deletes a resource.
- The resource is most often serialized into JSON.

### Spring Boot REST
- `@RESTController`: 
   - Combines `@Controller` and `@ResponseBody`.
- `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`: method-level annotations that instrument methods to handle different types of requests.
- `@ResponseBody`: 
   - is capable of serializing a returned Object into JSON.
- `@RequestBody`
   - is capable of deserializing incoming JSON data into the fields of an object.
- `@PathVariable`: extracts a variable from the provided path.
- `ResponseEntity<Object>`:
   - object is serialized into JSON before being sent off.
   - can also return an HTTP status code. See [Mozilla Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).
- `@JsonFormat`: can configure how properties get serialized. The following example serializes the annotated field into a JSON STRING, with a pattern of `dd-MM-yyyy hh:mm:ss`.
```
    @JsonFormat(shape = JsonFormat.Shape.STRING, pattern = "dd-MM-yyyy hh:mm:ss")
```
- `@Valid`: validates fields based on your constraints

## Exception Handling
- `@ControllerAdvice:` class-level annotation that allows you to define global exception handlers.
- `handleMethodArgumentNotValid`: method that can be overridden from the `ResponseEntityExceptionHandler` parent class. You can handle field violations and get the `BindingResult` here.
- `@ExceptionHandler`: method-level annotation that defines an exception handler.

![06f9dfba-89bc-420b-93e2-4d152fac8ff8.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F05fa3dd5-6750-47ac-9f52-c51dac2d67c2?alt=media&token=6b0df370-0ebf-43ae-a821-0d7993331c1b)
1. Define the exception that you want the method to handle.
2. Pass the exception into the list of arguments.


--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!

