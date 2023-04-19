# Challenge

**Goal**: validate the `Item` fields before submitting the form.

## Launch the Starter Project

![Screen Shot 2022-08-15 at 9.40.16 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F658c67a9-0d57-46b0-9bf8-767f1bbece25?alt=media&token=c6ef5181-ff53-4931-be1f-6668cb789194)

## Task 1
Add the validation dependency.
```xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-validation</artifactId>
    </dependency>
```
The `validation` dependency provides the library of files needed to validate fields.

## Task 2
Apply the following constraints to each field:
- If the submitted `category` is blank, display: `"Please choose a category"`
- If the submitted `name` is blank, display: `"Name cannot be blank"`
- If the submitted `price` is less than 0, display: `Price cannot be negative`.
- If the submitted `discount` is less than 0, display: `Discount cannot be negative`.
- If the submitted `date` is not in the past, display: `Date must be in the past`.

![Screen Shot 2022-06-02 at 9.05.32 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F04da9acc-8f42-45b2-99a0-dcea96b26d19?alt=media&token=d082410b-71f2-4e6d-a2b7-dc3adbd36e06)

## Task 3

Upon returning the form, the drop-down list loses its data. 

![Screen Shot 2022-06-05 at 5.14.11 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fb20f616a-00c5-4453-b913-73ebf05c760a?alt=media&token=071a1012-edc3-41f6-9cef-b3ade9829ffb)

Since the data is fixed:
- Remove the `model.addAttribute("categories", categories)` line from your handler method.
 - It makes more sense to write the values directly inside the HTML. 

```html
     <option style="color:blue" value="">Choose Category</option>
     <option style="color:blue" value="Furniture">Furniture</option>
     <option style="color:blue" value="Office Supplies">Office Supplies</option>
     <option style="color:blue" value="Technology">Technology</option>
```
### Output
---

![Screen Shot 2022-05-25 at 8.06.56 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F39123c63-a3de-4662-9499-8b63c25e6663?alt=media&token=b9abe5e6-aaee-4edb-8390-88c4c0cc2925)


## Task 4

Remove the `CATEGORIES` constant from `Constants.java`. It was only there for you to practice Thymeleaf loops, but its presence in the backend is not useful.

## Task 5

The `price` cannot be less than the `discount`. Apply cross-field validation to the `price` and `discount`. 

![Screen Shot 2022-06-02 at 9.10.26 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F0350222f-9e52-41ab-9497-9b34d0103a58?alt=media&token=aeb2645d-b2e2-4daf-ad63-f19fe4498469)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!