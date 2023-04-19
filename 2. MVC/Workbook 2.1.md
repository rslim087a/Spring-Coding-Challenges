# Workbook 2.1

Create a Spring Boot project.
| Group Id | Artifact Id | Dependencies |
| --- | --- | --- |
| `com.ltp` | `workbook` | `Spring Web`,  `Spring Boot DevTools`|

## Task 1

Create a method that can handle GET requests on path `/`, and returns a view called `shows`.

## Task 2

Create an HTML file under the templates folder called `shows.html`. It will display the following header:

```
 <h2>IMDB: Top 5 Episodes</h2>
```
## Task 3
Run the application and make a request.

![Screen Shot 2022-06-17 at 6.43.39 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F948d5d40-410d-4917-b25b-c8db2b668875?alt=media&token=0f8c867b-dc65-47c7-85bf-85373f1ec41c)

The **Thymeleaf** dependency is needed to work with templates. Add it to your POM file. 
```html
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```

## Task 4

Using the cheat sheet, create a table that displays the following data


| Title | Episode | Rating |
| --- | --- | --- |
| Breaking Bad | Ozymandias | 10.0 |
| Attack on Titan | Hero | 9.9 |
| Attack on Titan | Perfect Game | 9.9 |
| Star Wars: The Clone Wars | Victory and Death | 9.9 |
| Mr. Robot | 407 Proxy Authentication Required | 9.9 |

Give your table a `width` of `100%` and a `solid` `border`.


![Screen Shot 2022-05-21 at 1.16.16 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fb0ddcde7-fca4-42ba-a682-741c947ea925?alt=media&token=5414cea9-f663-41c7-b231-513f5064a412)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!