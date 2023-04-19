# Challenge – Part 2

There is an imbalance in the `course_student` relationship.

## Launch the Starter Project

![Screen Shot 2022-08-08 at 11.45.45 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe8e7994f-cc29-4894-ba95-1dc250b98d43?alt=media&token=2bbd7a09-6a50-4969-a5c6-a38bb73be248)

## Task 1

Make 4 `PUT` requests:

```
localhost:8080/course/1/student/1
localhost:8080/course/5/student/1

localhost:8080/course/1/student/2
localhost:8080/course/6/student/2

```

![Screen Shot 2022-08-08 at 6.46.02 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F23ffb106-6568-47b3-9469-260649d73836?alt=media&token=f576c9de-7926-414d-a1fe-0024fbfa6bfe)

## Task 2

Delete the course with an ID of 5. It gets deleted in the course table.

![Screen Shot 2022-08-08 at 8.00.05 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F84016e41-d772-41ae-acd0-4f176dd51b38?alt=media&token=60db05da-0dec-4ec6-a77e-45b41935441d)

Because `course` owns the association, associated records are deleted in the join table as well.

![Screen Shot 2022-08-08 at 8.08.21 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fed71ade4-d3dc-46ae-991a-56c6a7283306?alt=media&token=14374da9-1d02-4640-b4d9-532f89aa1a71)


Now, try deleting the student with an id of 2.
```json
{
    "timestamp": "08-08-2022 07:19:05",
    "message": [
        "Data Integrity Violation: we cannot process your request."
    ]
}
```
Ideally, deleting a student would also remove associated records in the join table.

![Screen Shot 2022-08-08 at 7.35.30 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F399c57cc-00b8-437f-ba6c-fd05f07637e2?alt=media&token=611b3c84-f5bc-45c7-a928-1a9c10392ff7)

But `student` is the non-owning side of the association, and cannot make changes to the join table.

## Task 3

In order for `student` to be equal in managing the relationship, you need to:

1. Remove `mappedBy`.
2. Make sure that `student` **owns** the join table as well. 
```java
    @JoinTable(
        name = "course_student",
        joinColumns = @JoinColumn(name = "student_id", referencedColumnName = "id"),
        inverseJoinColumns = @JoinColumn(name = "course_id", referencedColumnName = "id")
    )
```

## Task 4

Make 2 `PUT` requests:

```
localhost:8080/course/1/student/1
localhost:8080/course/1/student/2
```

Then delete the student with an id of 2.

![Screen Shot 2022-08-08 at 7.57.59 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F87e1dfa6-9356-4c19-905b-abe9e479cea0?alt=media&token=7bfffb68-6266-4cd6-b95a-b81df737ef51)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!