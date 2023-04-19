# Workbook 2.2

Inside your `spring-boot-bootcamp-resources`, follow this path to launch the starter project. 

![Screen Shot 2022-08-15 at 11.10.51 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F5bacdb18-4318-4d4e-a036-4e6a755b80d0?alt=media&token=5d298bb7-2380-4982-864c-705b9e3b0b22)

## Task 1

Create a POJO class for `Show` objects. The class will have three fields:

```java
    private String title;
    private String episode;
    private double rating;
```
Add the usual constructor, getters, and setters.

## Task 2

Before returning the view, add the following objects to the model:

```java
new Show("Breaking Bad", "Ozymandias", 10.0)
new Show("Attack on Titan", "Hero", 9.9)
new Show("Attack on Titan", "Perfect Game", 9.9)
new Show("Star Wars: The Clone Wars", "Victory and Death", 9.9)
new Show("Mr. Robot", "407 Proxy Authentication Required", 9.9)
```
## Task 3
Remove the hardcoded data inside `shows.html`. Use **variable expressions** to populate the view with data from the model.

![Screen Shot 2022-05-21 at 1.16.16 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fb0ddcde7-fca4-42ba-a682-741c947ea925?alt=media&token=5414cea9-f663-41c7-b231-513f5064a412)

## Task 4
The **variable expressions** can get a little verbose.
- Remove the variable expressions. 
- Bind a row to a model object.
- The underlying elements in each row can **select** a field from the previously bound object.
![Screen Shot 2022-05-21 at 1.16.16 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fb0ddcde7-fca4-42ba-a682-741c947ea925?alt=media&token=5414cea9-f663-41c7-b231-513f5064a412)


## Task 5

Remove the `Model model` parameter inside your handler method. 

## Task 6
In the olden days, the model was defined as a `HashMap`. Create a `HashMap` that can store key-value pairs of `String` and `Show`.

```java
    Map<String, Show> model = new HashMap<String, Show>();
    model.put("first", new Show("Breaking Bad", "Ozymandias", 10.0));
    model.put("second", new Show("Attack on Titan", "Hero", 9.9));
    model.put("third", new Show("Attack on Titan", "Perfect Game", 9.9));
    model.put("fourth", new Show("Star Wars: The Clone Wars", "Victory and Death", 	9.9));
    model.put("fifth", new Show("Mr. Robot", "407 Proxy Authentication Required", 9.9));
```

## Task 7

In the olden days, the `ModelAndView` return type was used instead of `String`. From your handler method, return `new ModelAndView("viewName", model)`. 

![Screen Shot 2022-05-21 at 1.16.16 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fb0ddcde7-fca4-42ba-a682-741c947ea925?alt=media&token=5414cea9-f663-41c7-b231-513f5064a412)


## Why did we do this?

It's good to be versatile. You never know when you'll encounter it.

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!