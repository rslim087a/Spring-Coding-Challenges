# Cheat Sheet

This cheat sheet contains important takeaways from section five.

## Beans and Dependency Injection

1. A bean is an object that lives inside the Spring Container.
3. As your `@SpringBootApplication` performs a `@ComponentScan`, a bean is created from classes marked with `@Component`.
4. `@Controller`, `@Service` and `@Repository` derive from `@Component`.
5. `@Configuration`: marks a class as a source for bean definitions.
6. `@Bean`: method-level annotation for bean definitions.
7. `@Autowired` injects the bean where it's needed.

## Defining Beans (Java)

```java
@Configuration
public class AppConfig {

    @Bean
    public SomeObject method() {
        return new SomeObject();
    }

}
```

## Defining Beans (XML)

`AppConfig.java` 
```java
@Configuration
@ImportResource("app-config.xml")
public class AppConfig {

}
```

`app-config.xml`

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

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!