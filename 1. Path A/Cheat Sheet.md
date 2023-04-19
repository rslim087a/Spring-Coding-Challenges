# Cheat Sheet

This cheat sheet contains important takeaways that lead up to section one.

## Introduction to Spring Boot

### Creating a Spring Boot Project with Maven
- `Group Id`: Identifies the organization (ex: **com.ltp**)
- `Artifact Id`: Determines the name of the application (ex: **hello-spring**)
- `Dependency`: Software that your application depends on.
### Maven Standard Directory Layout:

- `src/main/java`: source code.
- `src/main/resources`
   - `static`: images, CSS, static HTML.
   - `templates`: dynamic HTML templates.
   - `application.properties`: application properties and settings.
- `src/test/java`: application tests.

### Compiling and Running
- `mvnw spring-boot:run`: compiles and runs your application.
- `mvnw clean spring-boot:run`: cleans `target` folder, compiles, and runs your application.
- `mvnw package`: builds and packages the compiled classes into a `JAR` file.
- `java -jar`: runs the `JAR` file.

### Client-Server Model
1. **Client**: Entity making a request.
2. **Server**: Machine receiving the request.
3. **IP address**: Sequence of numbers that identifies a server.
4. **Port**: Tells the server where to forward the request.
5. **HTTP Server**: Software that processes requests.

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!