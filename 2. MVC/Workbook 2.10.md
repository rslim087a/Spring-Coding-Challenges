# Workbook 2.10

![Screen Shot 2022-08-15 at 11.21.05 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ff59eb27c-0a66-4857-89ce-72f83ba8aacb?alt=media&token=002060af-8cd2-4300-bb17-f86a274a544f)

## Task 1

Create a POJO class for `Employee` objects. The class will have three fields:
```java
    private String name;
    private int age;
    private String role;
```
Add the usual constructor, getters, and setters.

## Task 2

Before returning the view, add the following objects to the model:
```java
    List<Employee> employees = Arrays.asList(
        new Employee("Jim Halpert", 32, "Salesman"),
        new Employee("Andy Bernard", 38, "Salesman"),
        new Employee("Pam Beesly", 32, "Receptionist"),
        new Employee("Michael Scott", 49, "Regional Manager"),
        new Employee("Ryan Howard", 28, "Temp"),
        new Employee("Angela Martin", 35, "Accountant"),
        new Employee("Dwight Schrute", 37, "Assistant to the Regional Manager")
    );
```
## Task 3

Under the header in `staff.html`, create a table similar to the following:


| Name | Age | Role |
| --- | --- | --- |
| Data | Data | Data |
| Data | Data | Data |
| Data | Data | Data |

## Task 4

Using a Thymeleaf loop, your table must generate as many rows as there are objects in the `employees` list.

### **Expected Output:**
----
![Screen Shot 2022-05-22 at 5.32.13 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Febf37ff2-4070-4717-b078-23a2b4e31c3f?alt=media&token=679abe36-db4d-4dad-8285-2fcede6e888c)


## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!