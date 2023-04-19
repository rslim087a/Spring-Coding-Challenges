# Challenge – Part 2

**Goal**: Implement form submission.

## Task 1

Create a POJO `Item` class. An `Item` contains the following fields:

```java
    private String category;
    private String name;
    private Double price;
    private Double discount;
    private Date date;
```

Add an empty constructor, public getters, and public setters.

## Task 2

Create an `Item` object and bind it to the form.

## Task 3

Bind every form element to a field in the object.
```html
    <form method="post" th:object="${item}">
        <select class="select" th:field="*{category}">
            <option style="color:blue" value="">Choose Category</option>
            <option th:each="category: ${categories}" th:text="${category}" th:value="${category}"> Placeholder </option>
        </select>
	<!-- etc... -->
    </form>
```

## Task 4

Upon submission, your form must make a POST request on `/submitItem`.

## Task 5

Create a handler method that intercepts the POST request.
```java
    @PostMapping("/submitItem")
    public String handleSubmit(Item item) {

    }
```

Create an `ArrayList` that can store `Item` objects. 
```java
   private List<Item> items = new ArrayList<Item>();
```
- From your handler method, add a new `Item` object to the datastore.
- `redirect` the client to the `inventory` view.

## Task 6

Navigate to `localhost:8080`, and try to submit the form:

![Screen Shot 2022-05-25 at 9.11.11 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe63fe130-4935-42a0-a6d3-61def6c38d69?alt=media&token=73a0d42a-c5cb-4df5-8998-7e159bc6ab7c)

The time format of your `Date` field is different than the provided `yyyy-MM-dd` `String` from your form. 

![Untitled.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F87f40ed0-2eca-420c-a72e-c7703c003521?alt=media&token=7c5ba81b-098a-4ff5-ac5b-84d056a3aafc)

Your `Date` field must follow the same `DateTimeFormat` pattern.
```java
    @DateTimeFormat(pattern = "yyyy-MM-dd")
    private Date date;
```

## Task 7

I encourage you to watch the solution provided on Udemy. It goes through the full thought process behind solving this bug.

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!