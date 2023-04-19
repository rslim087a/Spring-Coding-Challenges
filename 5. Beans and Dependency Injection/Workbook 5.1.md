# Workbook 5.1

In the olden days, it was only possible to configure beans using XML.

## Launch the starter project

![Screen Shot 2022-08-16 at 1.36.20 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F94a00be9-e2b1-4388-ba82-2c622529da97?alt=media&token=ca2631f2-d712-48a8-be3c-415d746190de)

## Task 1

Create an `app-config.xml` file inside `/src/main/resources`.

## Task 2

Use the following template to configure the `Service` and `Repository` beans.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
	xmlns:context="http://www.springframework.org/schema/context"
	xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">

	<bean id="choose a name for the bean" class="path to class"> </bean>

	<bean id="choose a name for the bean" class="path to class"> </bean>
</beans>
```
An example of a path is: `com.organization.artifactid.folder.ClassName`

## Task 3
There is an `AppConfig` class inside the source code. It has already been configured to scan for beans inside `app-config.xml`.

```java
@Configuration
@ImportResource("app-config.xml")
public class AppConfig {

}
```
## Task 4
Remove the `@Service` and `@Repository` annotations, otherwise Spring Boot will throw an exception. The beans are already being configured inside `app-config.xml`. 


---
**Final Remarks**: I prefer the Java implementation.

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!