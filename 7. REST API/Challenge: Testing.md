# Challenge

**Goal**: Write tests to verify that your operations meet the expected requirements. 

## Launch the Starter Project

![Screen Shot 2022-08-12 at 10.02.08 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F0afbeb29-a530-4d5d-986d-a08b07290440?alt=media&token=a05ed40e-2969-4779-9e66-753ada5a3839)

## Initial Remarks

- In the testing section, you learned how to write unit tests with `Mockito`, and integration tests with `MockMVC`. 

- The `Service` layer doesn't contain meaningful logic. So, we will not write any unit tests.
## Starter Project

The starter project includes two methods. 

`setup()` will run **`@BeforeEach`** integration test and populate the repository with data.

```java
    @BeforeEach
    void setup(){
        for (int i = 0; i < contacts.length; i++) {
            contactRepository.saveContact(contacts[i]);
	}
    }
```
`clear()` will run **`@AfterEach`** integration test and clear the repository.
```java
    @AfterEach
    void clear(){
        contactRepository.getContacts().clear();
    }
```

## Cheat Sheet

For the tasks that follow, feel free to use the cheat sheet from the **Testing** section.

## Test 1
Inside `getContactByIdTest`, mock a GET request to `/contact/1`.

---
### Four assertions will follow:

1. Assert that the response returned is **200**. 
     - **Hint:** see the [Documentation](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/test/web/servlet/ResultActions.html#andExpect-org.springframework.test.web.servlet.ResultMatcher-) for `andExpect()`.
 2. Assert that the returned content is of type `JSON`. 
     - **Hint:** see the [Documentation](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/test/web/servlet/ResultActions.html#andExpect-org.springframework.test.web.servlet.ResultMatcher-) for `andExpect()`.
----
### Side Note: `JsonPath`

>`JSONPath` allows you to query JSON. 

Assume that you have the following JSON structure:

```json
{
    "id": "971aa9ff-bdcc-4569-833a-87bb4d383a2d",
    "name": "Rayan",
    "phoneNumber": "5334221234"
}
``` 
Given the following query `jsonPath("$.name")`, the dollar sign refers to the root element.

![Screen Shot 2022-08-13 at 2.35.55 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fb274e511-5557-405f-91a2-5386082ab8d2?alt=media&token=82b6df04-05eb-4557-bbe6-53afdfdfc217)

The root element is simply the JSON document. So, `$.name` grabs the name of the root element.

![Screen Shot 2022-08-13 at 2.05.10 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F03b9779f-5726-4cb6-8578-2d1e85a86a76?alt=media&token=606da35c-d530-4ff6-9284-c0044e89bab5)

---
**Using this information:**

3. Assert that the `name` returned by the JSON response equals the **correct value**. Feel free to see the [Documentation](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/test/web/servlet/ResultActions.html#andExpect-org.springframework.test.web.servlet.ResultMatcher-) for a working example.
4. Assert that the `phoneNumber` returned by the JSON response equals the **correct value**.

**Run your test:**

![Screen Shot 2022-08-13 at 2.10.30 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F47f0f768-7dd9-4105-ab52-3799f31f93fe?alt=media&token=6475cb1a-4bed-424e-b3e8-4a81390688ef)


## Test 2
Inside `getAllContactsTest`, mock a GET request to `/contact/all`.

---
### Four assertions will follow:
1. Assert that the response returned is 200. 
     - **Hint:** see the [Documentation](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/test/web/servlet/ResultActions.html#andExpect-org.springframework.test.web.servlet.ResultMatcher-) for `andExpect()`.

 2. Assert that the returned content is of type `JSON`. 

     - **Hint:** see the [Documentation](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/test/web/servlet/ResultActions.html#andExpect-org.springframework.test.web.servlet.ResultMatcher-) for `andExpect()`.

----
### Side Note: `JsonPath`

Assume that you have the following JSON **Array**:

```json
[
    {
        "name": "Jon Snow",
        "age": 25
    },
    {
        "name": "Tyrion Lannister",
        "age": 40
    },
    {
        "name": "The Hound",
        "age": 40
    }
]
``` 
Because the root element is an Array, you can use `$.size()` to count the number of documents. 

-----

**Using this information:**

3. Assert that the size of the returned JSON collection is correct.

---
### Side Note: `JsonPath`

The following query checks for the existence of a JSON document with:
- an age of 25. 
- a name of Jon Snow.

```java
jsonPath("$.[?(@.age == 25 && @.name == \"Jon Snow\")]").exists()
```
----

**Final Assertion**

We expect `getContacts()` to return the following JSON:

```json
[
    {
        "id": "1",
        "name": "Jon Snow",
        "phoneNumber": "6135342524"
    },
    {
        "id": "2",
        "name": "Tyrion Lannister",
        "phoneNumber": "4145433332"
    },
    {
        "id": "3",
        "name": "The Hound",
        "phoneNumber": "3452125631"
    }
]
```

4. From the JSON collection that gets returned, make an assertion that checks for the existence of a document with:

      - `id` =  `"2"` 
      - `name` = `"Tyrion Lannister"`
      - `phoneNumber` = `"4145433332"`.

**Run your test:**

![Screen Shot 2022-08-13 at 2.44.33 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F60eb227b-3a50-4c56-8c93-68cfff12f7ff?alt=media&token=7a043f2d-d60f-4644-bcbd-cf43317891fd)



## Test 3
- Inside `contactNotFoundTest()`, mock a GET request to `/contact/4`.
- Assert that the response returned is **404**. 

![Screen Shot 2022-08-13 at 2.47.45 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F95896150-9d6e-4e77-acc6-7fdd0b1687e2?alt=media&token=558a5294-30cd-4464-af3d-46fcd49b399d)


## `ObjectMapper`

> Can convert any POJO to JSON.

For test 4, you will need to autowire the `ObjectMapper` bean inside your test class.

## Test 4

Inside `validContactCreation()`, mock a POST request to `/contact`.

-----
Assume that you want to send this JSON as part of the request body:
```json
{
    "name": "Jon",
    "age": "25"
}
```
Inside your request builder, you can specify that the type of content you'll be sending is JSON.

```java
.contentType(MediaType.APPLICATION_JSON)
```
Inside your request builder, you can use `objectMapper` to serialize a Java Object into a `JSON` String.
```java
.content(objectMapper.writeValueAsString(new Student("Jon", 25)));
```
-----
**Using this information:** 

As you perform the request, send the following JSON as payload.
```JSON
{
    "id": null,
    "name": "Rayan",
    "phoneNumber": "5334221234"
}
```
Assert that the response returned is **201** (Created). 

![Screen Shot 2022-08-13 at 3.09.04 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F78d9758b-b3c9-44c0-8d34-999a7bd36e49?alt=media&token=1c4d990e-61e0-46bb-83bd-a38c2280047e)


## Test 5

- Inside `invalidContactCreation()`, mock a POST request to `/contact`.
- Send the following JSON as your POST request body.

```json
{
    "id": null,
    "name": "   ",
    "phoneNumber": "     "
}
```
- Assert that the response returned is **400**. 

![Screen Shot 2022-08-13 at 3.13.23 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F65b6c833-308c-4105-b7a3-a83a65238b6d?alt=media&token=1b11a41b-6ca4-4178-82ff-d87fb629c904)


## Congratulations!

By testing your API, you verified that every operation is working as it should.

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!