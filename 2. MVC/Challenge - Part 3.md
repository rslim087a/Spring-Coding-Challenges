# Challenge – Part 3

**Goal**: Implement the update functionality.

## Task 1

Every update button inside the table must make a GET request to the homepage. 

```html
th:href="@{/}"
```

## Task 2

Every item that gets submitted should carry an `id`.

```java
public class Item {
    //...
    private String id;

    public Item() {
        this.id = UUID.randomUUID().toString();
    }

    public String getId() {
        return this.id;
    }

    public void setId(String id) {
        this.id = id;
    }

    //...

}
 ```
Upon pressing update, the GET request needs to include an **`id`** parameter that identifies the selected item.
```html
 th:href="@{/(param = ${element.field})}"
```
Submit another item to the inventory table. Then, press **update**.

![Screen Shot 2022-08-17 at 5.40.10 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F2ae9b873-0ecf-4b3e-b68e-6b9c105712aa?alt=media&token=0f090045-4569-449f-824d-022b37c15414)
---
**Output**: the parameter should get carried over

![Screen Shot 2022-08-17 at 5.41.48 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Faa1c5fcd-1495-4749-a199-4e9a55be25ab?alt=media&token=21ab59e5-d9b0-4e7e-809a-e68bd208ebd2)
---

Print the `id` inside the handler method, and repeat the process.
```java
public String getForm(Model model, @RequestParam(required = false) String id) {
    //...
    System.out.println("id: " + id);
    //...
    return "form";
}
```

**Terminal Output:** `id: 5500b7d3-73ac-4d1d-9596-1b5bbca3cae1`

## Task 3

Before returning the `form` view, check if the `id` matches any of the items inside the data store.


```java
public String getForm(Model model, @RequestParam(required = false) String id) {
    
                  // if there is a match
    if (match) {  
        model.addAttribute("item", matching object);
    } 

    else {      // if there is no match
        model.addAttribute("item", new Item());
    }

     //etc...
}
```

In there is a match, your form elements will pre-populate with values from the model attribute.

![Screen Shot 2022-06-05 at 1.37.33 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F4287194b-b9bf-45ff-b172-f79590d1a4a1?alt=media&token=6a983e3c-9dc2-43d0-aed3-cc87ed69c00a)

## Task 4

1. Upon form submission, make sure the **id** is part of the POST request payload. 
```html
<input type="hidden" th:field="*{YOUR_ID_FIELD}">
```
2. **(Optional)**: Inside `handleSubmit()`, confirm that the item's `id` is being received.

3. Use the `id` to check if the submitted item already exists
     - If so, your handler method must **update** the datastore.
     - Otherwise, your handler method must **add** to the datastore.

4. Redirect the client to the `inventory` view.
5. Test both scenarios before moving to the next task.
## Task 5

>**`FlashAttribute`**: Data that survives a redirect.

Inside `Constants.java`, create another constant called `SUCCESS_STATUS`.
```
public static final String SUCCESS_STATUS = "success";
```
Inside `handleSubmit()`, add the following parameter: 
```java
(Item item, RedirectAttributes redirectAttributes)
```


Before redirection, add a `FlashAttribute` with key: **`status`** and value: **`Constants.SUCCESS_STATUS`**. 

```java
redirectAttributes.addFlashAttribute("status", Constants.SUCCESS_STATUS);
```


After redirecting the client to `/inventory`, the `FlashAttribute` will populate `Model model`.

```java
    @GetMapping("/inventory")
    public String getInventory(Model model)
```

## Task 6

Display the following `div` **only** if `status` equals `success`.

```HTML
    <div class="alert success">
        <strong> You successfully submited the item! </strong> 
    </div> 
```

![Screen Shot 2022-06-02 at 2.38.39 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F89601440-bd3a-4acd-a299-2d8d80531992?alt=media&token=45db3b2c-e039-407e-a11c-2711ef79a479)
    

## Task 7

Your next task is to forbid **updates** if the new `orderDate` has a 5-day discrepancy from the previous one. 

![Screen Shot 2022-06-02 at 3.08.54 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F2ac50b3d-225e-4f01-b339-ead22966bbda?alt=media&token=79467186-6e51-43cc-b456-7738aec5f433)

Inside `Constants.java`, create another constant called `FAILED_STATUS`.

```java
public static final String FAILED_STATUS = "failed";
```
The following method returns `true` if two dates are within 5 days.

```java
    public boolean within5Days(Date newDate, Date oldDate) {
        long diff = Math.abs(newDate.getTime() - oldDate.getTime());
        return (int) (TimeUnit.MILLISECONDS.toDays(diff)) <= 5;
    }
```
The next step is to update `handleSubmit()`

```java
    @PostMapping("/submitItem")
    public String handleSubmit(Item item, RedirectAttributes redirectAttributes) {


    }
```
1. The `status` variable starts off equaling `success`.


```java
    @PostMapping("/submitItem")
    public String handleSubmit(Item item, RedirectAttributes redirectAttributes) {

        int index = getIndexFromId(item.getId());   

        /****************** 1 ******************/

        String status = Constants.SUCCESS_STATUS;
```
2. If the `id` doesn't have a match, the submitted item gets added to the datastore.

```java
    @PostMapping("/submitItem")
    public String handleSubmit(Item item, RedirectAttributes redirectAttributes) {

        int index = getIndexFromId(item.getId());   

        /****************** 1 ******************/

        String status = Constants.SUCCESS_STATUS;

        /****************** 2 ******************/

        if (index == Constants.NOT_FOUND) {
            items.add(item);
        }
```
3. If there is a match, and the updated date is within 5 days, the datastore gets updated.

```java
    @PostMapping("/submitItem")
    public String handleSubmit(Item item, RedirectAttributes redirectAttributes) {

        int index = getIndexFromId(item.getId());   

        /****************** 1 ******************/

        String status = Constants.SUCCESS_STATUS;

        /****************** 2 ******************/

        if (index == Constants.NOT_FOUND) {
            items.add(item);
        }

        /****************** 3 ******************/

        else if (within5Days(item.getDate(), items.get(index).getDate())){
            items.set(index, item);
        }

```


4. If there is a match, but the updated date is **not** within 5 days, nothing happens and the `status` variable equals `failed`.

```java
    @PostMapping("/submitItem")
    public String handleSubmit(Item item, RedirectAttributes redirectAttributes) {

        int index = getIndexFromId(item.getId());   

        /****************** 1 ******************/

        String status = Constants.SUCCESS_STATUS;

        /****************** 2 ******************/

        if (index == Constants.NOT_FOUND) {
            items.add(item);
        }
        /****************** 3 ******************/

        else if (within5Days(item.getDate(), items.get(index).getDate())){
            items.set(index, item);
        }


        /****************** 4 ******************/

        else {
            status = Constants.FAILED_STATUS;
        }

        redirectAttributes.addFlashAttribute("status", status);
        return "redirect:/inventory";
    }
```




---
### HTML

Add a Thymeleaf attribute that displays the `div` **only** if the `status` attribute equals `failed`.

```HTML
     <div class="alert">
          <strong > You failed to submit the item. </strong> 
     </div>
```

Finally, try updating an item's date beyond the 5-day threshold. 

![Screen Shot 2022-06-02 at 3.08.54 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F2ac50b3d-225e-4f01-b339-ead22966bbda?alt=media&token=79467186-6e51-43cc-b456-7738aec5f433)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!