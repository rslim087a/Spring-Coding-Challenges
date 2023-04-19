# Workbook 3.1

Using the Spring Initializr, create a new project with the following dependencies:

1. `spring-boot-starter-web`
2. `spring-boot-devtools`
3. `spring-boot-starter-thymeleaf`
4. `spring-boot-starter-validation`

Feel free to assign your own Group Id and Artifact Id.

## Task 1

Create a Controller class with two methods:

```java
    @GetMapping("/")
    public String getForm(Model model) {
        return "sign-up";
    }
```


```java
    @GetMapping("/result")
    public String getResult() {
        return "result";
    }
```
## Task 2

Inside `spring-boot-bootcamp-resources` > `3.field-validation` > `workbook-3.1` > `starter`, grab the font file and the stylesheet.

![Screen Shot 2022-08-15 at 8.56.19 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F8b966120-aeb1-4144-aa67-25ca6ea74f7b?alt=media&token=a25f74f2-da9b-407e-b926-7e738dc63157)

-  Under your `static` folder, create a `fonts` folder and place the font file inside.
- Place the stylesheet under your `static` folder.

![Screen Shot 2022-08-15 at 8.56.58 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F7728b81c-6dd6-4910-a2a0-e4349d3d37dd?alt=media&token=52bda611-b0ed-4a71-aed3-4396c936fbf5)

## Task 3

Under the `templates` folder:
- Create a `sign-up.html` file. 
- Title the document `Sign Up`, and link the stylesheet.

```html
    <head>
        <title>Sign Up</title>
        <link rel="stylesheet" th:href="@{/form-stylesheet.css}">
    </head>
```
-  Create a `result.html` file. 
- Title the document `Result`, and give it one header that displays: Success. 

```html
    <head>
        <title>Result</title>
    </head>
    <body>
        <h1>Success</h1>       
    </body>
```

## Task 4

Inside the `sign-up` page, create a `div` and link it to the CSS `"container"` class.
```html
<div class="container">

</div> 
```

## Task 5

Inside the `div` container, add an `<h2>` header that displays Javagram. The CSS is already configured to use the billabong font.

![Screen Shot 2022-05-21 at 4.35.00 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F05356584-98d6-40d1-80af-cb9da9d31b95?alt=media&token=cb09bce9-2776-4c40-8e76-54e40c82b608)

## Task 6

Under the header, add a form with:
 - `method="post"`
 - input of `type` `text` and `placeholder` `First Name`.
 - input of `type` `text` and `placeholder` `Last Name`.
 - input of `type` `text` and `placeholder` `Username`.
 - input of `type` `text` and `placeholder` `Email`.
 - paragraph with `style="font-weight: bold"` formatting  that displays `Date of Birth`.
 - input of `type` `date`.
 - produce two line breaks using `<br><br>`.
 - input of `type` `submit` and `value` `Submit`.
### Input
```html
        <form method="post">
            <input type="text" placeholder="First Name">
            <input type="text" placeholder="Last Name">
            <input type="text" placeholder="Username">
            <input type="text" placeholder="Email">
            <p style="font-weight: bold">Date of Birth</p>
            <input type="date"> <br><br>
            <input type="submit" value="Submit">                
        </form>
```

### Output

![Screen Shot 2022-05-21 at 4.48.58 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F9019c0ae-352f-4d1d-a81c-57c74cc8c216?alt=media&token=64395c2a-9c07-435d-850e-4eb2a918f3f9)


## Task 7

Create a POJO class for `User` objects with fields that match the form elements.

```java
public class User {

    private String firstName;
    private String lastName;
    private String userName;
    private String email;
    private Date dateOfBirth;

    //Generate a complete constructor.
    //Generate an empty constructor.
    //Generate getters and setters.
}
```

## Task 8

Bind the form to an empty `User` object.
```html
<form method="post" th:object="${user}">


</form>
```

Each input must bind to a `field` from the object.

```html
<form method="post" th:object="${user}" th:action="@{/submitItem}">
    <input type="text" placeholder="First Name" th:field="*{firstName}">
    <input type="text" placeholder="Last Name" th:field="*{lastName}">
    <input type="text" placeholder="Username" th:field="*{userName}">
    <input type="text" placeholder="Email" th:field="*{email}">
    <p style="font-weight: bold">Date of Birth</p>
    <input type="date" th:field="*{dateOfBirth}"> <br><br>
    <input type="submit" value="Submit">                
</form>
```

## Task 9

Your form must submit POST requests on `/submitItem`. 

## Task 10

Create a handler method named `handleSubmit()` that receives the POST request and re-directs the client to the `result` view.

## Task 11

Using the annotations table from the cheat sheet, ensure that:
- First and last names are not blank with at least two characters.

```html
    //Example: 
    @NotBlank(message = "First name cannot be blank")
    @Size(min = 2, message = "First name is too short")
```
- Username is not blank and is at least 7 characters.
- Email is valid **(see cheat sheet)**.
- The date is in the past **(see cheat sheet)**.

If the user violates any of these constraints, return the `sign-up` page, and use the following template to display errors.
```HTML
<p style="color:red" th:errors="*{field of selected object}"></p>
```

Test your application by submitting invalid data. 

![Screen Shot 2022-05-21 at 7.03.09 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F8af1dc9a-118f-4ba2-b631-3b88abf9196a?alt=media&token=dfdc9329-520b-42f0-a400-e95f81d8f870)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!