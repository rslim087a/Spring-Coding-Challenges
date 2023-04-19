# HTML Cheat Sheet

As a Spring Boot developer, your main concern is the backend. 

>**Front End**: Graphical interface of a website written in HTML and CSS. 

>**Backend**: Server-side logic that stores and manages data.

You are not expected to know HTML. Use this cheat sheet as a guide.

## Useful Definitions:
- `block`: takes up the entire width.
- `inline`: only takes up the necessary width.
- `Container Tag`: contains an opening tag and a closing tag.
   - `opening tag`:  **`<p>`**`Hello`
   - `closing tag`: `<p>Hello`**`</p>`**
   - Content exists between the opening and closing tag.
   - `<p>`**`Hello`**`</p>`

- `Empty Element`: Does not need a closing tag.    
   - **`<img`**` src="mona-lisa"`**`>`**
   - **`<link`**` href="path"`**`>`**
   - **`<input`**` type="text"`**`>`**
   - **`<br>`**
   - You can optionally add a closing slash **`<img`**` src="mona-lisa"`**`/>`**.
# Metadata
- `<head>`: contains metadata.
- `<title>`: title of the document.
- `<style>`: you can define CSS here.
- `<link>`: links an HTML template to an external resource. 
     - `Empty Element`.
     - `th:href` = `"path-to-resource"`
     - `rel = "relationship to document"`
```html
<link th:href="@{/path-starts-from-static}" rel="stylesheet">
```

# Visual Elements
- `<body>`: contains the visual elements.
```html
<body>

   //visual elements go here.
  
</body>
```
## Container 
> `<div>` is a container that groups HTML content.
```HTML
  <div>
    <h1>Hello</h1>
    <p>Spring</p>
  </div>
```
> `<div>` is **block-level**.
```HTML
    <div>Hello</div>
    <div>Spring</div>
```
![Screen Shot 2022-06-12 at 4.58.29 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F76a11337-6071-4dd9-a5a8-c06b9c865570?alt=media&token=38277873-d3ee-4bad-9fd7-7714ef504bdd)
## Span Container

> `<span>` is also a container that groups HTML content.
``` HTML
<span>
  <h1>Hello</h1>
  <p>Spring</p>
</span>
```
> `<span>` is an **inline** element.
```HTML
    <span>Hello</span>
    <span>Spring</span>
```
![Screen Shot 2022-06-12 at 4.59.08 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F94741f8e-b2ee-4ea1-bc89-78ef6b66c345?alt=media&token=f1c5261e-a270-4298-88c9-45b251d2bf01)

## **Headers**
### `<h1>` ... `<h6>`.

![Screen Shot 2022-06-18 at 2.19.29 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F05af4a58-5a5e-4a34-84de-641b082acd83?alt=media&token=46e4764e-ece4-4d75-bc95-f0595d88049c)
## Text
> `<p>` is **block**-level text.
```HTML
    <p>Spring</p>
    <p>Boot</p>
    <p>Development</p>
    <p>Bootcamp</p>
```
![Screen Shot 2022-06-12 at 4.59.57 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F83bd6f76-f0e3-46d6-a998-914bb35002c6?alt=media&token=6fbbb299-2062-4254-8a59-ee41ed168e4c)


## Images

- `<img>`: displays an image.
   -  `Empty Element`.
   - `src = "path"`.
   - `alt= "alternative text if image fails to show"`.

**Layout**

![Screen Shot 2022-06-15 at 2.45.54 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F68a4e144-d483-49c0-ae74-27d1c7d064bc?alt=media&token=398927e3-944c-4105-b049-7bfde1d61729)

 **Code**
```HTML
    <img src="images/A.png" alt="A"/>
    <img src="images/B.png" alt="B"/>
    <img src="images/C.png" alt="C"/>
    <img src="images/D.png" alt="D"/>
```
 **Output**

![Screen Shot 2022-06-12 at 5.11.58 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F962fdfc8-4d61-48ef-838f-87c1f5b4a145?alt=media&token=479cb9aa-2991-4d8d-96e6-9291aada705a)

## Table
- `<table>`: displays a table.
- `<tr>`: table row (one table can contain many rows).
- `<th>`: header cell (one row can contain many headers).
- `<td>`: data cell (one row can contain many data cells).

```HTML
    <table border="solid" width="300">
        <tr>
           <th>House</th>
           <th>Name</th>
           <th>Position</th>
        </tr>
        <tr>
           <td>Gryffindor</td>
           <td>Harry</td>
           <td>Seeker</td>
        </tr>
        <tr>
           <td>Slytherin</td>
           <td>Crabbe</td>
           <td>Beater</td>
        </tr>
        <tr>
           <td>Hufflepuff</td>
           <td>Cedric</td>
           <td>Seeker</td>
        </tr>
    </table>

```
![Screen Shot 2022-06-12 at 5.21.49 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc20fd1c8-19ce-4e83-ab3d-1cdc0dab961e?alt=media&token=d18efee1-9b31-435e-b119-1dcf2138cf30)

## Lists
- `<ul>`: unordered list.
- `<ol>`: ordered list.
- `<li>`: items in a list.
```HTML
    <ol>
        <li>Pancakes: $2.99</li>
        <li>Eggs: $3.29</li>
        <li>Bacon: $4.99</li>
    </ol>        
```
![Screen Shot 2022-06-12 at 5.25.36 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Faf4a414a-e3ca-43c2-a118-5d4d70adeb3f?alt=media&token=fff05f93-78a1-4895-846c-d9a815ec61e1)

## Form
- `<form>`: defines an HTML form for user input.
- `<input>`: defines an input for the form.
    - `Empty Element`.
    - `type="text"`: input is a textfield.
   - `type="date"`: input is a date.
   - `type="submit"`: input is a submit button. 
   - `type="hidden"`: hides the input. 

-  `<br>`: produces a Line Break

```HTML
    <form>
        <input type="text" placeholder="First Name">
        <input type="text" placeholder="Last Name">
        <p> Date of Birth </p>
        <input type="date"><br><br>
        <input type="submit" value="Submit">
    </form> 
```
![Screen Shot 2022-06-12 at 5.35.17 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F71bb5c1a-79d3-41bf-b756-39a9b807ecc3?alt=media&token=d9f3550b-5e75-46a0-9db8-a2f6699bdc68)



## Hyperlink
- `<a>`: defines a hyperlink.
  - `th:href = "@{/url endpoint}"`: GET request to relative path.
  - `th:href = "@{/url endpoint(parameter = value)}"`: GET request to relative path while passing in a parameter.
  -  `role="button"`: anchor tag takes the role of a button.

## Common HTML Attributes
> HTML attributes are specified in the opening tag.
- `class`: assigns an HTML element to a class in a stylesheet.
- `width`: controls the width of an element.
- `height`: controls the height of an element.
- `border`: controls the border of an element (usually `none`, or `solid`)
- `style`: adds styling. For example: `"style="color:red"`
- `th:style`: the styling depends on a Thymeleaf expression.
```HTML
        <table border="solid" width="100%">
          <tr>
            <th>Item</th>
            <th>Revenue</th>
            <th>Cost</th>
            <th>Profit</th>
          </tr>
          <tr style="background: green">
            <td>Table</td>
            <td>200</td>
            <td>49</td>
            <td>151</td>
          </tr>
          <tr style="background: red">
            <td style="color: white">Table</td>
            <td style="color: white">49</td>
            <td style="color: white">200</td>
            <td style="color: white">-151</td>
          </tr>
        </table>
```
![Screen Shot 2022-06-12 at 5.44.37 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F2a058d68-5451-483c-95e2-ee16711cd1c3?alt=media&token=5d85a1ac-0e58-492b-aba3-1712a2100ef9)

## Thymeleaf Counterparts 
> The counterpart can equal the result of a thymeleaf expression.
 - Variable Expression: `${...}`
 - Selection Expression: `*{...}`
 - Link Expression: `@{...}`

| Normal | Counterpart | Example |
| --- | --- | --- |
| `href` | `th:href` | `<link th:href="@{path-to-resource-from-static}"`|
| `href` | `th:href` | `<a th:href="@{url-endpoint(param='value')}"`|
| `src` | `th:src` | `<img th:src="@{path-to-image}"`|
| `style` | `th:style` | `<p th:style="${condition} ? 'str' : 'str'"`|
| `value` | `th:value` | `<option th:value="${modelAtt}">`|

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!