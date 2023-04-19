# Workbook 2.3

![Screen Shot 2022-08-15 at 11.13.17 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fbec816aa-3011-4d66-8607-a15e5717eae5?alt=media&token=574ef2bf-a753-4e88-9851-8db5f4836163)
## Task 1

Add a `speed` of `45` as a model attribute.
```java
    model.addAttribute("speed", 45);
```
## The `+` operator
>You can add values using the `+` operator.
```html
    th:text="${modelAttribute} + ${modelAttribute}"
```
It will concatenate strings.
```java
            //hello             //spring
th:text="${modelAttribute} + ${modelAttribute}"
>> Result: hello spring 
```
It will add numbers.
```java
            //5             //5
th:text="${modelAttribute} + ${modelAttribute}"
>> Result: 10 
```
Use  **single quotes** for plain text. 
```html
th:text="'plain text' + ${modelAttribute}"
```

## Task 2
Inside `sign.html`, create a header element that displays the speed:

![Screen Shot 2022-05-21 at 2.25.06 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F954d1ea0-d051-41a2-8e43-0f3dae49dfe5?alt=media&token=0caea4c4-d99a-4df9-81d1-5e0d418f119e)
-------


## Task 3
1. Create an image element that displays `slow-down` **only** if the speed is higher than 60. 
2. Use `th:if` or `th:unless`.
3. Give the image a width of 200.

## Task 4
1. Create an image element that displays `speed-limit` if the speed is lower than 60. 
2. Use `th:if` or `th:unless`.
3. Give the image a width of 200.

### Test case 1
----
![Screen Shot 2022-05-21 at 2.30.36 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F21722841-17b5-4488-b9d4-912d91637493?alt=media&token=053f22d3-2acb-4696-b1c5-eb0a7e0a1fde)
### Test case 2
----
![Screen Shot 2022-05-21 at 2.32.14 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fa85d2b78-0201-4818-a1b7-d304dfe31738?alt=media&token=01983d45-31be-4358-9c0c-c0baa69ebbd6)


## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!