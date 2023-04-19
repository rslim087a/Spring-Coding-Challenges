# Workbook 2.11

![Screen Shot 2022-08-15 at 11.21.51 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F877b7720-24ba-4c90-b111-b0b53bddb887?alt=media&token=cc0c9137-9c50-49ee-8176-a1a0e0b1a690)

## Task 1

Create a POJO class for `Record` objects. The class will have three fields:
```java
    private String item;
    private double revenue;
    private double cost;
```
Add the usual constructor, getters, and setters.

## Task 2

Before returning the view, add the following objects to the model:
```java
    List<Record> records = Arrays.asList(
        new Record("Chair", 20.99, 5.99),
        new Record("Table", 40.99, 8.99),
        new Record("Couch", 100.99, 105.99),
        new Record("Fridge", 200.99, 59.99),
        new Record("Bed", 150.99, 205.99)  
    );
```
## Task 3

Under the header in `records.html`, create a table similar to the following:


| Item | Revenue | Cost | Profit |
| --- | --- | --- | --- |
| Data | Data | Data | Data |
| Data | Data | Data | Data |
| Data | Data | Data | Data |

## Task 4

Using a Thymeleaf loop, your table must generate as many rows as there are objects in the `records` list. 

![Screen Shot 2022-05-22 at 6.18.40 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F27e416d3-bb59-40c0-90d7-0b788119e040?alt=media&token=c0162243-226b-433c-b52d-a312bf215008)

**Hint:** For the `Profit` rows, Thymeleaf allows you to subtract using the `-` operator. 

## Task 5

`double` is not suitable for storing currency because it has a certain precision. `BigDecimal` is an exact way of representing numbers.

### 1 Update your POJO class accordingly.
----
```java
    private String item;
    private BigDecimal revenue;
    private BigDecimal cost;
```
### 2 Use this `List` instead.
---
```java
    List<Record> records = Arrays.asList(
        new Record("Chair", new BigDecimal("20.99"),  new BigDecimal("5.99")),
        new Record("Table",  new BigDecimal("40.99"),  new BigDecimal("8.99")),
        new Record("Couch",  new BigDecimal("100.99"),  new BigDecimal("105.99")),
        new Record("Fridge",  new BigDecimal("200.99"),  new BigDecimal("59.99")),
        new Record("Bed",  new BigDecimal("150.99"),  new BigDecimal("205.99"))
    );
```
### **Expected Output:**
----
![Screen Shot 2022-05-22 at 6.57.54 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F0f64ff43-3ab5-4480-9101-e74bbb85c76a?alt=media&token=7949713a-3478-45b5-9a44-9a2bd6803a13)

## Task 6

Common types from which Thymeleaf can leverage utility methods are:
- `#dates` 
- `#strings`
- `#arrays`
- `#lists`
- `#numbers`

Inside [Thymeleaf Repo](https://github.com/thymeleaf/thymeleaf/blob/3.1-master/lib/thymeleaf/src/main/java/org/thymeleaf/expression/Numbers.java), the `Numbers` class has a utility method that can format the model attribute into a currency. 

![Screen Shot 2022-08-16 at 12.50.38 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc1c71eb6-5471-4a11-9e34-196a5c99b48d?alt=media&token=1ddc86cf-5daa-4671-ab84-a0efb99c22bb)

Using this information, try to achieve the following output: 
![Screen Shot 2022-05-22 at 7.04.00 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F413ac9cb-912e-4cad-b6fa-8e78c8b631ce?alt=media&token=aaa60680-4761-426c-933c-db42759f2d51)

## Task 7
You can use `th:style` to format an HTML element. 

- `th:style` must equal `background: green` if `profit` is greater than or equal to 0. 
- Otherwise, it must equal `background: red`.


![Screen Shot 2022-05-22 at 7.14.33 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc66e7e7e-346a-4364-a88f-c04bc77b0881?alt=media&token=25845c2d-6dd4-423e-95ce-0c294a0d47f5)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!