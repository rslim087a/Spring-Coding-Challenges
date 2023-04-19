# Workbook 9.4
The purpose of this workbook is to apply exception handling.

## Launch the Starter Project

![Screen Shot 2022-08-04 at 1.19.22 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ffaddffee-6907-4cfb-9121-e40bd926eb4b?alt=media&token=41613fd9-3a84-4f05-a55e-a18033ffbba1)

## Custom Annotation

The starter project comes with the custom annotation `@Score`. It is identical to the annotation from the field validation section.

## Error Response

The starter project also comes with an `ErrorResponse` template. It is identical to the template from the `REST API` section. 

## Global Exception Handler

The starter project also comes with a global exception handler. It inherits the method: `handleMethodArgumentNotValid` just like in workbook 8.3. 


## Task 1 (Review)
Apply validation constraints for:
- **Course**
   - If the submitted `subject` is blank: `message = "Subject cannot be blank"`
   - If the submitted `code` is blank: `message = "Course code cannot be blank"`
   - If the submitted `description` is blank: `message = "Description cannot be blank"`

- **Student**
   - If the submitted `name` is blank: `message = "Name cannot be blank"`
   - If the submitted `birthDate` is not in the past: `message = "The birth date must be in the past"`
- **Grade**
    - Apply the `@Score` constraint to the `score` field. 

## Task 2 (Review)
Inside the `CourseController`, `GradeController`, and `StudentController`, apply the `@Valid` annotation where needed.


## Task 3 (Review)
Create a global exception handler class. 

## Task 4 (Review)

Inside `handleMethodArgumentNotValid`:

1.  access the errors from the validation process through the binding result:
```java
ex.getBindingResult().getAllErrors()
```
2. append every error into an `ErrorResponse` object.
3. Return the `ErrorResponse` with a status code of 400.

## Task 5

Make a POST request on `localhost:8080/student`

```json
{
    "birthDate": "2040-07-31"
}
```

**Response:** 400 Bad Request

```json
{
    "timestamp": "05-08-2022 03:27:41",
    "message": [
        "Name cannot be blank",
        "The birth date must be in the past"
    ]
}
```

## Task 6

Make a POST request on `localhost:8080/grade/student/3/course/5`

```json
{
    "score": "R+"
}
```

**Response:** 400 Bad Request

```json
{
    "timestamp": "05-08-2022 03:33:15",
    "message": [
        "The score is not valid"
    ]
}
```

## Task 7

Make a POST request on `localhost:8080/course`

```json
{
    "subject": "    ",
    "code": "     ",
    "description": "      "
}
```

**Response:** 400 Bad Request

```json
{
    "timestamp": "05-08-2022 03:34:26",
    "message": [
        "Description cannot be blank",
        "Course code cannot be blank",
        "Subject cannot be blank"
    ]
}
```

##  Task 8

Create **one** exception handler method for an array of exceptions: 

```
    @ExceptionHandler({CourseNotFoundException.class, GradeNotFoundException.class, StudentNotFoundException.class})
    public ResponseEntity<Object> handleResourceNotFoundException(RuntimeException ex) 
``` 
1. Return a status code of 404.
2. Return an `ErrorResponse` template of the error.

##  Task 9

Make a GET request on `localhost:8080/student/10`

**Response:** 404 Not Found

```json
{
    "timestamp": "05-08-2022 03:37:35",
    "message": [
        "The student id '10' does not exist in our records"
    ]
}
```

##  Task 10

Make a GET request on `localhost:8080/grade/student/10/course/10`

**Response:** 404 Not Found

```json
{
    "timestamp": "05-08-2022 03:38:52",
    "message": [
        "The grade with student id: '10' and course id: '10' does not exist in our records"
    ]
}
```

## Task 11

An unsuccessful deletion will throw an `EmptyResultDataAccessException`.  Create an exception handler for it: 

```java
    @ExceptionHandler(EmptyResultDataAccessException.class)
    public ResponseEntity<Object> handleDataAccessException(EmptyResultDataAccessException ex) {

    }
``` 

The method will return an `ErrorResponse` template with a message: `Cannot delete non-existing resource`, followed by a a status code of 404. 
```java
    ErrorResponse errorResponse = new ErrorResponse(Arrays.asList("Cannot delete non-existing resource"));  
```

## Task 12

Make a DELETE request on `localhost:8080/course/10`

**Response:** 404 Not Found

```json
{
    "timestamp": "05-08-2022 03:49:33",
    "message": [
        "Cannot delete non-existing resource"
    ]
}
```

## Task 13

Attempting to save the same grade twice throws a `DataIntegrityViolationException`. Create an exception handler for it: 

```java
@ExceptionHandler(DataIntegrityViolationException.class)
public ResponseEntity<Object> handleDataIntegrityViolationException(DataIntegrityViolationException ex)
``` 

Return an `ErrorResponse` template with a message: `Data Integrity Violation: we cannot process your request`, followed by a status code of 400. 

## Task 14
Try saving the same grade twice.

```json
{
    "timestamp": "05-08-2022 03:55:37",
    "message": [
        "Data Integrity Violation: we cannot process your request."
    ]
}
```

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!