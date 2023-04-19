# Workbook 3.2

Individually, each field is valid. But from a cross-field point of view, the user isn't taking the submission process seriously.

![Screen Shot 2022-05-21 at 7.32.27 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F4eaad5c8-4461-47da-a5ff-1e29e0e709bd?alt=media&token=3bd5ef3c-bbde-4e44-af79-b8274227b878)

**Goal:** You will use cross-field validation to ensure the user isn't entering garbage data. 


## Task 1

The following code rejects a field and adds an error to the `BindingResult`.
```java
bindingResult.rejectValue(arg1, arg2, arg3):
  // Argument 1: The field value you wish to reject.
  // Argument 2: Error Code
  // Argument 3: Error message.
```
---
**Using this information**:
1. reject the `lastName` if it happens to equal the `firstName`. 
2. Leave the error code empty `""`.
3. Display the error message: `please enter valid data`.


![Screen Shot 2022-05-21 at 7.53.42 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fdd838862-c676-4041-838c-5a595d266b3d?alt=media&token=352414a8-8794-4901-bc08-5978c280adcd)

# Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!