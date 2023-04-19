# Workbook 9.2

The `grade-submission` API will serve as a mediator between a consumer and the resources in an SQL database.

![Screen Shot 2022-07-21 at 6.49.32 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F3e565790-0fd0-4a2e-aeee-854d516c83b3?alt=media&token=0241d76f-0e82-4e4d-b510-52b2af59a46c)

Workbook 9.2 will prepare the REST endpoints for the `GradeController`.

![Screen Shot 2022-07-21 at 6.55.45 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc2e756b0-22b4-4700-a2b3-157fb45073f7?alt=media&token=5affb776-f7e8-44a8-9833-3ab3afb18412)

## Intermission

Workbooks 9.2 and 9.3 are the same as 9.1.

- If you don't need to further practice REST, skip them.

- Otherwise, feel free to solve them.

The completed project can be found here:

![Screen Shot 2022-09-26 at 7.53.27 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F75fb775f-9210-4cdc-835c-92d1935e4297?alt=media&token=d98df8a0-a5f3-40b2-8835-2521d478a414)
A Postman collection will be provided in the lesson: "Saving a Student"

## GET Request
- method handles GET requests made on `/grade/student/{studentId}/course/{courseId}`.
- return type: `ResponseEntity<Grade>`.
- name: `getGrade`.
- path variables: `Long studentId, Long courseId`.
- returns a `ResponseEntity` with no data and a status of 200.

### Postman

- Create a request called `Read Grade`.
- Make a GET request.
**Response:** 200 OK.


## POST Request
- method handles POST requests made on `/grade/student/{studentId}/course/{courseId}`.
- return type: `ResponseEntity<Grade>`.
- name: `saveGrade`.
- **deserializes** incoming JSON properties into a `Grade` object.
- path variables: `Long studentId, Long courseId`.
- returns a `ResponseEntity` which **re-serializes** the object into a JSON with a status code of 201.

### Postman

- Create a request called `Create Grade`.
- Make a POST request that sends the following JSON:

```json
{
    "score": "A+"
}
```

**Response:** 201 Created

```json
{
    "id": null,
    "score": "A+"
}
```

## PUT Request
- method handles PUT requests made on `/grade/student/{studentId}/course/{courseId}`.
- return type: `ResponseEntity<Grade>`.
- name: `updateGrade`.
- **deserializes** incoming JSON properties into a `Grade` object.
- path variables: `Long studentId, Long courseId`.
- returns a `ResponseEntity` which **re-serializes** the object into a JSON with a status code of 200.

### Postman

- Create a request called `Update Grade`.
- Make a PUT request that sends the following JSON:

```json
{
    "id": 1,
    "score": "A+"
}
```

**Response:** 200 OK

```json
{
    "id": 1,
    "score": "A+"
}
```


## DELETE Request
- method handles DELETE requests made on `/grade/student/{studentId}/course/{courseId}`.
- return type: `ResponseEntity<HttpStatus>`.
- name: `deleteGrade`.
- path variables: `Long studentId, Long courseId`.
- returns a `ResponseEntity` with a status code of 204.

### Postman

- Create a request called `Delete Grade`.
- Make a DELETE request.
**Response**: 204 No Content.

## GET Request
- method handles GET requests made on `/grade/student/{studentId}`.
- with return type: `ResponseEntity<List<Grade>>`.
- name: `getStudentGrades`.
- path variable: `Long studentId`.
- returns a `ResponseEntity` with a status code of 200.

### Postman

- Create a request called `Read Student Grades`.

- Make a GET request.
**Response:** 200 OK.


## GET Request
- method handles GET requests made on `/grade/course/{courseId}`.
- with return type: `ResponseEntity<List<Grade>>`.
- name: `getCourseGrades`.
- path variable: `Long courseId`.
- returns a `ResponseEntity` with a status code of 200.

### Postman

- Create a request called `Read Course Grades`.
- Make a GET request.
**Response:** 200 OK.

## GET Request
- method handles GET requests made on `/grade/all`.
- with return type: `ResponseEntity<List<Grade>>`.
- name: `getGrades`.
- returns a `ResponseEntity` with a status code of 200.

### Postman

- Create a request called `Read Grades`.
- Make a GET request.
**Response:** 200 OK.

## Final Touches

Save every request

![Screen Shot 2022-07-22 at 1.28.29 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F97188181-4f87-41d2-afc8-001a0a5de427?alt=media&token=4705d1b1-1806-4ffb-816d-07232d9b44a0)

Create a new folder called Grade. Drag every `Grade` request there.

![Screen Shot 2022-07-22 at 2.05.31 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F2d86f41b-b7fe-40ca-a8d8-b3059b297af1?alt=media&token=5666ae2f-8605-4427-babd-a1aa74f4c299)


## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!