# Challenge – Part 2 (follow-up)

In this challenge, you will apply utility methods inside your templates.
## Task 1

The `inventory` page starts with static data. Populate the inventory table with data from the datastore.
### Controller
```java
    @GetMapping("/inventory")
    public String getInventory(Model model) {
        model.addAttribute("items", items);
        return "inventory";
    }
```
### Template

```html
         <tr |LOOP|>
            <td th:text="${element.field}"> </th>
            <td th:text="${element.field}"> </td>
            <td type="currency" th:text="${element.field}"> </td>
            <td type="currency" th:text="${element.field}"> </td>
            <td type="date" th:text="${element.field}"> </td>
            <td>
              <a role="button" style="color:white; background-color: #263238" class="table-button">Update</a>
           </td>
        </tr>
```

**Output:**

From the homepage, try to submit an item.

![Screen Shot 2022-06-02 at 4.00.49 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe2414ecc-d580-41c3-b199-1f888e065151?alt=media&token=9f5b9367-ff9b-48ef-9904-896c7f8ec618)

`th:text` displays a tedious `toString` representation of your `Date`.

## Task 2: Option A (Not Recommended)


Add another method to your POJO class.
```java
    public String getFormatDate() {
        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd");
        return formatter.format(date);   
    }
```

Use **`th:text = "${element.formatDate}"`** to fetch the formatted date from  `getFormatDate()`.

![Screen Shot 2022-06-02 at 4.01.15 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F95e3b840-44ff-49b4-b7b7-443ad06af2c0?alt=media&token=7007c66a-9be2-46e3-b5b0-4203966d3d40)

## Task 3: Option B (Recommended)

>You should format visual output using Thymeleaf. 

The `Dates` class (`#dates`) from the [Thymeleaf Repo](https://github.com/thymeleaf/thymeleaf/blob/3.0-master/src/main/java/org/thymeleaf/expression/Dates.java) contains a **format** method that accepts two arguments:

**1.** The date you are formatting.

**2.** The pattern used to format it.

![Screen Shot 2022-08-16 at 1.08.22 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F8d27a065-84c7-4eb7-8cca-fbba4fd6098b?alt=media&token=4e069929-9af0-47ab-b4ec-2ef4a9d72f6c)

Using this information, format your date to a pattern of  `'yyyy-MM-dd`'

![Screen Shot 2022-06-02 at 4.01.15 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F95e3b840-44ff-49b4-b7b7-443ad06af2c0?alt=media&token=7007c66a-9be2-46e3-b5b0-4203966d3d40)

## Task 4
Remove the `type="currency"` attribute for `price` and `discount`. Use the `formatCurrency` method provided by `#numbers`.

![Screen Shot 2022-08-17 at 2.31.34 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F627a4470-4683-4b98-a480-663e67661d90?alt=media&token=4175cbde-c7d6-4e14-b866-e9bf70827566)
## Good Luck!


--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!