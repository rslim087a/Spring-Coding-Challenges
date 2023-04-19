# Challenge

There is a **Many** to **Many** relationship between the `course` and `student`  tables.

## Launch the Starter Project

![Screen Shot 2022-08-06 at 4.58.09 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F33b15884-ef5e-4349-886c-4b9faa2ec27d?alt=media&token=69dea308-cde9-48ca-9702-ffeaa7868825)

## One to Many

One student can have **Many** grades. Many grades belong to **One** student.

![Screen Shot 2022-08-06 at 5.03.20 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F38905fc8-5998-4f9a-bdb9-e5daaf837c0a?alt=media&token=288db1f0-6879-4e90-88ce-1ee9555c6f4a)

The `student_id` **column** joins both tables.

![Screen Shot 2022-08-06 at 5.19.09 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc679b140-bf10-4d8f-b842-569f9fc15767?alt=media&token=3e46b877-3a5d-4313-8cab-df9d0d786504)

## One to Many

One course can have **Many** grades. Many grades belong to **One** course.

![Screen Shot 2022-08-06 at 5.07.32 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe9423cd8-8a1b-448f-91db-50edbd6449a5?alt=media&token=08ff9886-becb-40fd-91ac-6b0931b7184c)

The `course_id` **column** joins both tables.

![Screen Shot 2022-08-06 at 5.20.45 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F2a895a9e-a473-417d-ad79-d135627902e6?alt=media&token=1548361d-e475-4887-8d20-668222418c4d)


## Many to Many

One student can enroll in **Many** courses. One course can contain **Many** students.

![Screen Shot 2022-08-06 at 6.20.07 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F01702ef1-8a9b-4a7d-afc9-b1356bf58497?alt=media&token=8197124b-f3c8-43f8-87ce-6bdc35e16463)


The `course_student` **table** joins both tables. 

Harry took four courses.

![Screen Shot 2022-08-07 at 11.25.57 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ffa54d0f6-28c8-4b00-bcae-49e150dd569f?alt=media&token=9aab6023-3e4b-46c1-9f12-9260d7eb255d)

Hermione took four courses.

![Screen Shot 2022-08-06 at 6.21.04 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F8c86d62e-5680-4be7-a159-9ff4191da529?alt=media&token=6894fb44-e9a0-4dc1-9f8d-cbef72a6f432)

Herbology contains three students.

![Screen Shot 2022-08-06 at 6.21.51 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F603d5370-e817-4e24-9aae-32c96d34a175?alt=media&token=08938cea-e472-4b4f-96bf-ad9fab17a974)

Alchemy contains four students.

![Screen Shot 2022-08-06 at 6.22.45 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F928c922e-ee7f-4aaf-9907-0c28b6eb60d6?alt=media&token=64808c83-52b5-43d0-a3e7-f036a5071745)

The table that joins `course` and `student` is called a **Join Table**.

## Task 1

Inside `Course`, declare a `@ManyToMany` relationship with a `List` of students.

```java
    @ManyToMany
    private List<Student> students;
```
## Task 2

Inside `Student`, declare a `@ManyToMany` relationship with a `List` of courses.

## Who will own the association?
 
In the **One** to **Many** relationship between `student` and `grade`, the foreign key lives inside `grade`.

![Screen Shot 2022-08-06 at 5.19.09 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc679b140-bf10-4d8f-b842-569f9fc15767?alt=media&token=3e46b877-3a5d-4313-8cab-df9d0d786504)

As a result, `grade` owns the association.

```java
@Table(name = "grade")
public class Grade {

    @ManyToOne
    @JoinColumn(name = "student_id", referencedColumnName = "id")
    private Student student;

}
```


In the **One** to **Many** relationship between `course` and `grade`, the foreign key column lives inside `grade`.

![Screen Shot 2022-08-06 at 5.20.45 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F2a895a9e-a473-417d-ad79-d135627902e6?alt=media&token=1548361d-e475-4887-8d20-668222418c4d)

As a result, `grade` owns the association.

```java
@Table(name = "grade")
public class Grade {

    @ManyToOne
    @JoinColumn(name = "student_id", referencedColumnName = "id")
    private Student student;

```

In a **Many** to **Many** relationship, the joining columns live inside of the join table.

![Screen Shot 2022-08-06 at 6.42.32 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fa081f633-296d-4d1e-b5ef-46677744ec67?alt=media&token=09d8441b-59d1-48e0-9d0a-c9338ec568df)

So it doesn't matter who owns the association.

## Task 3

For the sake of this exercise, `Course` will own the association. Followed by its `@ManyToMany` annotation, define a `@JoinTable`.

![Screen Shot 2022-08-06 at 7.02.12 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F653b29f5-89be-4e02-aa06-72b6c7bf040a?alt=media&token=75f5e48f-d522-41d7-9751-49f68331220d)

1. Set the name equal to `course_student`

The parameters that follow define the join table's foreign key columns. Each foreign key column references the primary key of one table.

![Screen Shot 2022-08-18 at 4.53.55 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fa2143620-2877-49a4-b62e-42fc932839e9?alt=media&token=3dcc61c2-720a-469c-af02-f4cb531809e6)

2. Set `joinColumns` equal to a foreign key column `@JoinColumn` that references the primary table of the entity owning the association.
2. Set `inverseJoinColumns` equal to a foreign key column `@JoinColumn` that references the primary table of the entity that does not own the association.

### **Expected output**
---
![Screen Shot 2022-08-08 at 12.03.05 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F8af9af7a-0784-4fa2-937b-a4116442d52f?alt=media&token=20d64b66-bfea-4e93-abec-9b36258f224c)

The `course_student` join table appears, but Spring Boot creates another one by default.

## Task 4

Place the `mappedBy` parameter on the non-owning side of the relationship. 

### **Expected output**
---

![Screen Shot 2022-08-15 at 11.44.58 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F6c23b3e2-5b09-4613-8316-10813898d791?alt=media&token=2dc6280d-43dc-43bf-b60b-74ddaa6d1d7d)

## Task 5
In order to avoid a recursive loop, add `@JsonIgnore` to at least one side of the relationship. For this exercise, add it to the non-owning side.

```java
    @JsonIgnore
    @ManyToMany(mappedBy = "students")
    private List<Course> courses;
```

## Task 6

Inside the `CourseServiceImpl`, finish writing the code for `addStudentToCourse`:

```java
    //TODO...
    course.getStudents().add(unwrappedStudent);
    return courseRepository.save(course);
```

## Task 7

Inside the `CourseController`, finish writing the code for `enrollStudentToCourse`.

## Task 8

From Postman, create a new PUT request under the `Course` folder.

![Screen Shot 2022-08-08 at 12.38.46 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc5bb093d-25e6-42ba-b83d-79dd13b7fb7a?alt=media&token=724ecf93-5116-45b2-9dd6-1171a24faeb5)

Make four PUT requests to `localhost:8080/course/1/student/(1 to 4)`.

**Postman Output**

```json
{
    "id": 1,
    "subject": "Charms",
    "code": "CH104",
    "description": "In this class, you will learn spells concerned with giving an object new and unexpected properties.",
    "students": [
        {
            "id": 2,
            "name": "Ron Weasley",
            "birthDate": "1980-03-01"
        },
        {
            "id": 3,
            "name": "Hermione Granger",
            "birthDate": "1979-09-19"
        },
        {
            "id": 4,
            "name": "Neville Longbottom",
            "birthDate": "1980-07-30"
        },
        {
            "id": 1,
            "name": "Harry Potter",
            "birthDate": "1980-07-31"
        }
    ]
}
```

### H2 Output

![Screen Shot 2022-08-07 at 12.14.40 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F4037d1de-462f-4d4a-bc60-2491f777c0c6?alt=media&token=cf398b5c-63fd-4b19-bf89-69101d80ded6)

## Task 9

Currently, you can assign a course duplicate students. Try adding Ron to Charms twice.

![Screen Shot 2022-08-08 at 1.14.36 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F504c9151-7725-4dc0-96c1-be6d74ddcd7b?alt=media&token=7f7d9575-eba3-4044-b73f-1cd997355292)

In both POJO classes, replace the `List` collection type with a `Set`. A `Set` is a collection type that prevents the addition of duplicate elements. A student cannot enroll in duplicate courses.
```
private Set<Course> courses;
```

Similarly, a course cannot contain duplicate students.
```
private Set<Student> students;
```

Once again, test your application by trying to duplicate Ron's enrollment in charms.

## Task 10

- Inside `CourseServiceImpl`, finish writing the `getEnrolledStudents()` method.
- Inside `CourseController`, finish writing the `getEnrolledStudents()` handler method.
- Inside `StudentServiceImpl`, finish writing the `getEnrolledCourses()` method.
- Inside `StudentController`, finish writing the `getEnrolledCourses()` handler method.

## Task 11

1. From Postman, create a new GET request under the `Student` folder.

![Screen Shot 2022-08-07 at 1.14.34 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F16980a7c-62b8-4d23-9d8f-ba2ae2a823fa?alt=media&token=6c82d3ac-9d47-40c1-bcaf-cd0b51e437a8)

2. From Postman, create a new GET request under the `Course` folder.

![Screen Shot 2022-08-07 at 1.17.07 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F64ab2cbd-393c-44ef-a5e6-0b0f4f97a245?alt=media&token=9715187b-0554-4877-8742-2e8652caeb61)

## Task 12

Whenever we query a course, we want to exclude the collection of students from the JSON. Otherwise, the response will be messy and convoluted. Put the `@JSONIgnore` annotation on the owner side too.
```java
    @JsonIgnore
    @ManyToMany
    @JoinTable(
        name = "course_student",
        joinColumns = @JoinColumn(name = "course_id", referencedColumnName = "id"),
        inverseJoinColumns = @JoinColumn(name = "student_id", referencedColumnName = "id")
    )
    private Set<Student> students;
```

## Task 13

Make 12 `PUT` requests:
  - Enroll Harry in Charms and Potions.
  - Enroll Ron in History of Magic and Transfiguration
  - Enroll Hermione in Charms, History of Magic, Potions, and Transfiguration
  - Enroll Neville in Charms, Potions, and Herbology.

```
localhost:8080/course/1/student/1
localhost:8080/course/5/student/1

localhost:8080/course/4/student/2
localhost:8080/course/6/student/2

localhost:8080/course/1/student/3
localhost:8080/course/4/student/3
localhost:8080/course/5/student/3
localhost:8080/course/6/student/3


localhost:8080/course/1/student/4
localhost:8080/course/5/student/4
localhost:8080/course/3/student/4
```

**Output**

![Screen Shot 2022-08-07 at 12.33.42 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F4a888c71-6ad8-4199-a95b-6f7fe7a68fc2?alt=media&token=6dd6103e-18f6-443d-acfa-39ec59410bd6)

From Postman, read all of the courses that Harry is enrolled in:

```json
[
    {
        "id": 1,
        "subject": "Charms",
        "code": "CH104",
        "description": "In this class, you will learn spells concerned with giving an object new and unexpected properties."
    },
    {
        "id": 5,
        "subject": "Potions",
        "code": "POT102",
        "description": "In this class, you will learn correct mixing and stirring of ingredients to create mixtures with magical effects."
    }
]
```

From Postman, read all of the courses that Hermione is enrolled in:


```json
[
    {
        "id": 1,
        "subject": "Charms",
        "code": "CH104",
        "description": "In this class, you will learn spells concerned with giving an object new and unexpected properties."
    },
    {
        "id": 4,
        "subject": "History of Magic",
        "code": "HIS393",
        "description": "In this class, you will learn about significant events in wizarding history."
    },
    {
        "id": 6,
        "subject": "Transfiguration",
        "code": "TR442",
        "description": "In this class, you will learn the art of changing the form or appearance of an object."
    },
    {
        "id": 5,
        "subject": "Potions",
        "code": "POT102",
        "description": "In this class, you will learn correct mixing and stirring of ingredients to create mixtures with magical effects."
    }
]
```

From Postman, read all of the students enrolled in Potions.

```json
[
    {
        "id": 1,
        "name": "Harry Potter",
        "birthDate": "1980-07-31"
    },
    {
        "id": 3,
        "name": "Hermione Granger",
        "birthDate": "1979-09-19"
    },
    {
        "id": 4,
        "name": "Neville Longbottom",
        "birthDate": "1980-07-30"
    }
]
```

## Task 14

Inside `GradeServiceImpl.saveGrade()`, throw a new `StudentNotEnrolledException()` if the client assigns a student a grade on a course they are not enrolled in.

```java
    @Override
    public Grade saveGrade(Grade grade, Long studentId, Long courseId) {
        Student student = studentRepository.findById(studentId).get();
        Course course = courseRepository.findById(courseId).get();

        //TODO: if student not enrolled in course, throw StudentNotEnrolledException

        grade.setStudent(student);
        grade.setCourse(course);
        return gradeRepository.save(grade);
    }
```
Handle the exception by adding `StudentNotEnrolledException.class` as an argument for  the `@ExceptionHandler`: `handleResourceNotFoundException`.
## Task 15

Enroll Harry in Charms. Then, give him an A+.
```JSON
{
    "id": 1,
    "score": "A+",
    "student": {
        "id": 1,
        "name": "Harry Potter",
        "birthDate": "1980-07-31"
    },
    "course": {
        "id": 1,
        "subject": "Charms",
        "code": "CH104",
        "description": "In this class, you will learn spells concerned with giving an object new and unexpected properties."
    }
}
```

Now, give him a grade on a course that he's not enrolled in.

```json
{
    "timestamp": "07-08-2022 01:03:57",
    "message": [
        "The student with id: '1' is not enrolled in the course with id: '2"
    ]
}
```

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!