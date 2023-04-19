# Workbook 9.3

The `grade-submission` API will serve as a mediator between a consumer and the resources in an SQL database.

![Screen Shot 2022-07-21 at 6.49.32 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F3e565790-0fd0-4a2e-aeee-854d516c83b3?alt=media&token=0241d76f-0e82-4e4d-b510-52b2af59a46c)

Workbook 9.3 will prepare the REST endpoints for the `CourseController`.

![Screen Shot 2022-07-21 at 6.55.45 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc2e756b0-22b4-4700-a2b3-157fb45073f7?alt=media&token=5affb776-f7e8-44a8-9833-3ab3afb18412)

## Rest Controller

The operations in `CourseController` are identical to the ones in `StudentController`. Copy the code below and perform the necessary imports.

```java
    @GetMapping("/{id}")
    public ResponseEntity<Course> getCourse(@PathVariable Long id) {
        return new ResponseEntity<>(HttpStatus.OK);
    }

    @PostMapping
    public ResponseEntity<Course> saveCourse(@RequestBody Course course) {
        return new ResponseEntity<>(course, HttpStatus.CREATED);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<HttpStatus> deleteCourse(@PathVariable Long id) {
        return new ResponseEntity<>(HttpStatus.NO_CONTENT);
    }

    @GetMapping("/all")
    public ResponseEntity<List<Course>> getCourses() {
        return new ResponseEntity<>(HttpStatus.OK);
    }
```

## Postman

### Request 1
- Create a request called `Read Course`.
- Make a GET request to `localhost:8080/course/1`.

**Response:** 200 OK

---
### Request 2
- Create a request called `Create Course`.
- Make a POST request that sends the following JSON:

```json
{
    "subject": "Potions",
    "code": "POT-1123",
    "description": "In this class, students learn the correct way to brew potions."
}
```

**Response:** 201 Created

```json
{
    "id": null,
    "subject": "Potions",
    "code": "POT-1123",
    "description": "In this class, students learn the correct way to brew potions."
}
```
---
### Request 3
- Create a request called `Delete Course`.
- Test your DELETE request.

### Request 4

- Create a request called `Read Courses`.
- Test your GET request.

## Final Touches

Save every request

![Screen Shot 2022-07-22 at 1.28.29 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F97188181-4f87-41d2-afc8-001a0a5de427?alt=media&token=4705d1b1-1806-4ffb-816d-07232d9b44a0)

Create a new folder called Course. Drag every `Course` request there.

![Screen Shot 2022-07-22 at 2.35.09 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F8a54252e-65d4-480e-99f6-12984195221d?alt=media&token=49f6868f-24cb-4ef8-b508-fa37a77fa65f)

**We're all set**. Now we can start communicating with an SQL database.

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!