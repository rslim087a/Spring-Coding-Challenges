# Workbook 8.1
A resilient API will send back a 4xx status code when it receives a bad request.
## Launch the starter project

![Screen Shot 2022-07-13 at 6.54.45 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F14dc61fc-c365-45ff-b504-88e915372c51?alt=media&token=0d3aa094-759e-4caf-b111-da0b0348205c)

## The Problem

If the consumer sends a bad request (passes an id that doesn't exist), the application fails and throws an unchecked exception during the runtime.

![Screen Shot 2022-07-13 at 10.12.52 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F126ff7bb-81bc-4988-aeae-81c6d6b1dd7a?alt=media&token=4bd49d91-f4bf-4c74-ae55-1ee3bc0499e0)


It responds with a status code of 500.

![Screen Shot 2022-07-13 at 10.09.05 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F7dd852f1-a19a-464d-9361-2f85fab6f74c?alt=media&token=bc3cedd3-3107-45d8-aca4-e29a912b1db9)

The 500 status code should be reserved for actual server failures due to unexpected scenarios, like high resource usage (CPU / Physical Memory), database-related failure, etc... 

If a consumer sends an `id` that doesn't exist, such a scenario should be expected. The developer must anticipate this scenario and ensure that the application does not fail. It must be fully equipped to handle the bad request and respond with a 4xx status code.

## Task 1

Create a new folder called `exception`. Inside the folder, create a `NoContactException` class.

![Screen Shot 2022-07-13 at 7.02.51 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F814d77c2-8221-455b-aca8-9e72cd630c5c?alt=media&token=d4ef45ca-74e3-44c0-be89-81392d3fd99a)

Use the following code to create a custom **checked** exception:

```java
public class NoContactException extends Exception { 

}
```
If you took our Java course, a checked exception forces you to:
- `try` to run a piece of code.
- `catch` the exception if it fails.

## Task 2

Modify the `findIndexById` function to throw the `NoContactException`.
```java
    private int findIndexById(String id) throws NoContactException {
        return IntStream.range(0, contactRepository.getContacts().size())
            .filter(index -> contactRepository.getContacts().get(index).getId().equals(id))
            .findFirst()
            .orElseThrow(() -> new NoContactException());
    }
```
## Task 3

Every `Service` function that calls `findIndexById()` is at risk of **throwing** a `NoContactException`.

Modify the interface methods inside `ContactService`.
```java
    Contact getContactById(String id) throws NoContactException;
    void saveContact(Contact contact);
    void updateContact(String id, Contact contact) throws NoContactException;
    void deleteContact(String id) throws NoContactException;
    List<Contact> getContacts();
```
Fix the errors inside `ContactServiceImpl`.

```java
    @Override
    public Contact getContactById(String id) throws NoContactException {
        return contactRepository.getContact(findIndexById(id));
    }

   // etc...
```

## Task 4

Inside the handler method: `getContact`, `try` to run the current code.

```java
     try {
         Contact contact = contactService.getContactById(id);
         return new ResponseEntity<>(contact, HttpStatus.OK);    
     }
```
`catch` the exception in the event of a failure.

```java
     catch (NoContactException e)
```
If there is a failure, which status code should we return? 
```java 
     return new ResponseEntity<>(CHOOSE_STATUS_CODE);    
```
Choose the most appropriate status code from [Mozilla Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses).

## Task 5

In similar fashion, handle the exceptions inside `updateContact` and `deleteContact`.

## Task 6

Test your API using Postman. First create the  following resources:
```json
{
    "name": "Jon Snow",
    "phoneNumber": "6129439432"
}

{
    "name": "The Hound",
    "phoneNumber": "4125429422"
}

{
    "name": "Tyrion Lannister",
    "phoneNumber": "4515429321"
}
```
### Test Case 1
---
- `GET: localhost:8080/contact/all`

- Status Code: 200

```json
[
    {
        "id": "392963d8-cd35-4b6a-a881-c759b744029a",
        "name": "Jon Snow",
        "phoneNumber": "6129439432"
    },
    {
        "id": "1e8c9503-3ce9-4d7a-b0f0-af4c25e6ecbd",
        "name": "The Hound",
        "phoneNumber": "4125429422"
    },
    {
        "id": "e8820ff1-d0cb-49fe-9bf3-8f0a4549fdb3",
        "name": "Tyrion Lannister",
        "phoneNumber": "4515429321"
    }
]
```
### Test Case 2
---
- `GET: localhost:8080/contact/123`

- Status Code: **`404 Not Found`**

### Test Case 3
---

- `PUT: localhost:8080/contact/123`
- Status Code: **`400 Bad Request`**

### Test Case 4
---
- `PUT: localhost:8080/contact/123`
```json
Request Body
{
    "name": "Tyrion Lannister",
    "phoneNumber": "4515429321"
}
```
- Status Code: **`404 Not Found`**

### Test Case 5
---
- `DELETE: localhost:8080/contact/123`
- Status Code: **`404 Not Found`**

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!