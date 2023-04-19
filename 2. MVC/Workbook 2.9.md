# Workbook 2.9

![Screen Shot 2022-08-15 at 11.20.36 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F1f28d254-8adb-4213-98a2-53cca289ac5f?alt=media&token=09525840-b1bc-4fe8-a810-d41754dcbdbb)

## Task 1
Link each template to the stylesheet.

## Task 2

Inside both documents:
- assign the `div` containing the `<a>` tags to the CSS class `topnav`.
- assign the `div` containing the `<h1>` to the class `container`.


## Task 3
- The `HOME` button must make a GET request to the relative path `/`. 
- The `AWAY` button must make a GET request to the relative path `/away`.

## Task 4
The CSS class `active` colors a button green. Assign each button the `active` class depending on which webpage is being displayed. 

```html

   <!--away-->

     <div class="topnav">
         <a th:href="@{/}">Home</a>
         <a th:href="@{/away}" class="active">Away</a>
     </div>

   <!--home-->

     <div class="topnav">
         <a th:href="@{/}" class="active">Home</a>
         <a th:href="@{/away}">Away</a>
     </div>
```

Toggle between the buttons.
### Test Case: Home page
----
![Screen Shot 2022-05-22 at 2.45.21 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F55d9521d-6760-42a6-a319-fa0b4abf037a?alt=media&token=129f0b98-7686-4853-b8c3-217434077888)

### Test Case: Away page
----
![Screen Shot 2022-05-22 at 2.45.29 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F26abfaef-19e5-4fd6-bea7-a6a2dfc03012?alt=media&token=a14b53f4-269d-4518-970a-1f6b8266f04b)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!