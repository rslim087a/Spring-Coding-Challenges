# Workbook 9.1

The `grade-submission` API will serve as a mediator between a consumer and the resources in an SQL database.

![Screen Shot 2022-07-21 at 6.49.32 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F3e565790-0fd0-4a2e-aeee-854d516c83b3?alt=media&token=0241d76f-0e82-4e4d-b510-52b2af59a46c)

Workbook 9.1 will prepare the REST endpoints for the `StudentController`.

![Screen Shot 2022-07-21 at 6.55.45 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc2e756b0-22b4-4700-a2b3-157fb45073f7?alt=media&token=5affb776-f7e8-44a8-9833-3ab3afb18412)

## Launch the Starter Project

![Screen Shot 2022-07-21 at 6.58.16 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F4ec3eb0f-64d5-410e-9e6a-d583209f293e?alt=media&token=9c0db0c3-c7e6-4502-8053-98204595f2b7)


## `@RequestMapping`
> maps a web request at the class or method level.

This code maps any web request that starts with `/student`  to the `StudentController` bean.

![Screen Shot 2022-07-21 at 7.06.42 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ffe77eb6a-6063-441c-b0b6-783b6c4fa720?alt=media&token=2b070176-7af8-4ba4-9b09-e28488fff0fd)

## GET Request
Create a method:
- that handles GET requests made on `/student`.
- with return type: `ResponseEntity<Student>`.
- named `getStudent`.
- that accepts a `@PathVariable Long id`.
- that returns a `ResponseEntity` with no data and a status of 200.

### Postman

Inside Postman, create a collection called: **Grade Requests**. 

![Screen Shot 2022-08-18 at 3.07.18 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F94e7a538-5809-4b1e-b6cc-3f53a0669222?alt=media&token=583769c0-388b-436c-943b-231bef565510)

![Screen Shot 2022-07-21 at 11.33.03 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F1aa11c49-4c7a-408c-a1d3-a7cb840efbf8?alt=media&token=c4037f7e-8e7b-4c6c-900f-e45cb35f0d8e)

Inside **Grade Requests**, create a request called `Read Student`.

![Screen Shot 2022-07-21 at 11.36.09 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe0b2666b-4d29-4d10-8493-4c9f65cd282e?alt=media&token=9ba8d06b-c7e3-42ad-ad97-a66222ed551e)

Make a GET request to `localhost:8080/student/1`

![Screen Shot 2022-07-21 at 11.37.24 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F25ae59fc-74af-4e76-9652-5d33d89166e6?alt=media&token=b9bed339-a378-4cb1-8a5d-ffe33f9220d6)

## POST Request
Create a method:
- that handles POST requests made on `/student`.
- with return type `ResponseEntity<Student>`
- named `saveStudent`
- that **deserializes** incoming JSON properties into a `Student` object.
- that returns a `ResponseEntity` which **re-serializes** the object into a JSON with a status code of 201.

### Postman

- Create a request called `Create Student`.
- Make a POST request that sends the following JSON:

```json
{
    "name": "Harry Potter",
    "birthDate": "1980-07-31"
}
```

**Response:** 201 Created

```json
{
    "id": null,
    "name": "Harry Potter",
    "birthDate": "1980-07-31"
}
```

## DELETE Request
Create a method:
- that handles DELETE requests made on `/student`.
- with return type `ResponseEntity<HTTPStatus>`.
- named `deleteStudent`.
- with `@PathVariable Long id`.
- returns a `ResponseEntity` with a status code of 204.

### Postman

- Create a request called `Delete Student`.

- Make a DELETE request.
**Response:** 204 No Content.

## GET Request
- method handles GET requests made on `/student/all`.
- return type: `ResponseEntity<List<Student>>`.
- name: `getStudents`.
- returns a `ResponseEntity` with a status code of 200.

### Postman

- Create a request called `Read Students`.

- Make a GET request.
**Response:** 200 OK.

## Final Touches

Save every request

![Screen Shot 2022-07-22 at 1.28.29 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F97188181-4f87-41d2-afc8-001a0a5de427?alt=media&token=4705d1b1-1806-4ffb-816d-07232d9b44a0)

Create a new folder called Student. Drag every `Student` request there.

![Screen Shot 2022-07-27 at 11.45.13 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F586ffad1-f84d-4c7c-8722-9a7075f559af?alt=media&token=eae343a6-f0c0-48b8-b228-98d5ee401229)
## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!