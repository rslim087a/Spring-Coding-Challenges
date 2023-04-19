# Challenge
The goal of this challenge is to loosely couple your code.

## Open the challenge

![Screen Shot 2022-08-16 at 1.38.03 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F0a78ccf0-11c2-40e1-a2af-cd39d0aabdbf?alt=media&token=8c1451b3-6ee4-4156-bbec-676dd344c51a)

## Task 1

As you loosely couple your code, configure the beans using one of these options:

1. `@Service` and `@Repository` annotations.
2. `@Bean` Definitions.
3. XML Configuration.

## Task 2

For this challenge, do not directly wire the beans into each field. Have a look at the `@Autowired` annotation's targets:

```
@Target({ElementType.CONSTRUCTOR, ElementType.METHOD, ElementType.PARAMETER, ElementType.FIELD, ElementType.ANNOTATION_TYPE})
@Retention(RetentionPolicy.RUNTIME)
```
Notice that `@Autowired` can also be applied to constructors. Your task is to add one constructor inside `Controller`, and another inside `Service`. Then,  inject the beans into the constructor using `@Autowired`.

## Task 3: Remove `@Autowired`

You can remove the `@Autowired` annotation. Spring Boot will automatically inject a dependency into the constructor when it runs. Try it out!

![Screen Shot 2022-06-22 at 3.21.48 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc015204d-8191-487d-aa03-75d3be648df6?alt=media&token=6eadf818-b202-4a5b-a47c-983661fa67fc)


## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!