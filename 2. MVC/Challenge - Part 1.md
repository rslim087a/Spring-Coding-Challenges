# Global Superstore


![Screen Shot 2022-08-16 at 12.53.05 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ff0ee6b1e-8d33-4b5c-9779-dd24d829ab51?alt=media&token=ecad8df5-6119-4971-85c9-12a065d46416)

## Task 1

Create a `Controller` class and assign it a name of your choice.

## Task 2

Map a GET request on path `/` to a handler method called `getForm()`. 
```java
    @GetMapping("/")
    public String getForm()
```
- The handler method must return the `form` view.
```java
    @GetMapping("/")
    public String getForm() {
        return "form";
    }
```

## Task 3

Before returning the `"form"` view, add `Constants.CATEGORIES` as a model attribute. 

```java
    @GetMapping("/")
    public String getForm(Model model) {
        model.addAttribute("categories", Constants.CATEGORIES);
        return "form";
    }
```

Inside the `form` template, use a **Thymeleaf Loop** to populate the drop-down list with values from the array. 

![Screen Shot 2022-05-25 at 8.06.56 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F39123c63-a3de-4662-9499-8b63c25e6663?alt=media&token=b9abe5e6-aaee-4edb-8390-88c4c0cc2925)

## Task 4
> In a drop-down list, every **`<option>`** needs to equal a **`value`**. 

The **`value`** attribute determines what will be sent upon form submission
### Example
----
If the user chooses the option "Capital of Canada", **Ottawa** will be sent upon form submission.
```HTML
<select>
  <option value="Ottawa">Capital of Canada</option>
  <option value="Paris">Capital of France</option>
</select>
```
----
In your case, the option that displays `Choose Category` must equal a blank value. 
```html
<option style="color:blue" value="">Choose Category</option>
```
Every `<option>` that follows must equal a value that matches the text it displays.
```
<option |Thymeleaf Loop| th:text= |Element in LOOP| th:value = |Element in LOOP|>   </option>
```

## Task 5

Map any GET request made on the path `/inventory` to a handler method called `getInventory`. 

```java
    @GetMapping("/inventory")
    public String getInventory()
```

The handler method must return the `inventory` view.

```java
    @GetMapping("/inventory")
    public String getInventory() {
        return "inventory";
    }
```


## Task 6
Inside both templates, ensure that:

- The `Form` button makes a GET request on path `/`.
- The `Inventory` button makes a GET request on path `/inventory`.

Run your application and toggle between the buttons.
![Screen Shot 2022-05-25 at 8.08.22 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fb711fccb-15c5-4597-8f06-6da774ec0de8?alt=media&token=cf3a40cc-8b86-43c6-b811-2b8f14c91288)


## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!