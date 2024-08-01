1. ### Loose Coupling
   **Answer:** Loose coupling means reducing the dependencies between components in a system, so changes in one component have minimal impact on others.

   **Easy to Remember:** Less dependency, more flexibility.

2. ### Dependency
   **Answer:** A dependency is an object that another object needs to function.

   **Easy to Remember:** Something you need to work.

3. ### IOC (Inversion of Control)
   **Answer:** Inversion of Control is a design principle where the control of objects or portions of a program is transferred to a container or framework.

   **Easy to Remember:** Framework takes control.

4. ### Dependency Injection
   **Answer:** Dependency Injection is a design pattern used to implement IoC, where the container injects dependencies into a class.

   **Easy to Remember:** Injecting what you need.

5. ### Examples of Dependency Injection
   **Answer:**
   1. **Constructor Injection:**
      ```java
      public class MyService {
          private final Dependency dependency;
          public MyService(Dependency dependency) {
              this.dependency = dependency;
          }
      }
      ```
   2. **Setter Injection:**
      ```java
      public class MyService {
          private Dependency dependency;
          public void setDependency(Dependency dependency) {
              this.dependency = dependency;
          }
      }
      ```

   **Easy to Remember:** Providing what you need through constructor or setter.

6. ### Auto Wiring
   **Answer:** Auto Wiring is a Spring feature that automatically injects dependencies without explicit configuration.

   **Easy to Remember:** Auto-injecting dependencies.

7. ### Important Roles of an IOC Container
   **Answer:**
   1. Managing the lifecycle of beans.
   2. Resolving dependencies.
   3. Configuring beans.

   **Easy to Remember:** Manages beans and their dependencies.

8. ### Bean Factory and Application Context
   **Answer:** 
   - **Bean Factory:** Basic container providing fundamental DI features.
   - **Application Context:** Advanced container providing more enterprise-specific functionality.

   **Easy to Remember:** Bean Factory is basic, Application Context is advanced.

9. ### Compare Bean Factory with Application Context
   **Answer:**
   - **Bean Factory:** Lazy initialization, less feature-rich.
   - **Application Context:** Eager initialization, more features (e.g., event propagation, AOP).

   **Easy to Remember:** Application Context > Bean Factory.

10. ### Create an Application Context with Spring
    **Answer:**
    - **XML Configuration:**
       ```java
       ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
       ```
    - **Java Configuration:**
       ```java
       ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
       ```

    **Easy to Remember:** Use XML or Java class to configure context.

11. ### Spring Search for Components or Beans
    **Answer:** Spring uses component scanning to find components or beans.

    **Easy to Remember:** Component scanning finds beans.

12. ### Component Scan
    **Answer:** Component scanning automatically detects and registers beans in the application context.

    **Easy to Remember:** Automatic bean registration.

13. ### Define Component Scan in XML and Java Configurations
    **Answer:**
    - **XML:**
       ```xml
       <context:component-scan base-package="com.example.package" />
       ```
    - **Java:**
       ```java
       @ComponentScan(basePackages = "com.example.package")
       ```

    **Easy to Remember:** Use `component-scan` in XML or `@ComponentScan` in Java.

14. ### Component Scan in Spring Boot
    **Answer:** Spring Boot automatically scans for components in the package of the main application class and its sub-packages.

    **Easy to Remember:** Automatic in Spring Boot.

15. ### @Component
    **Answer:** Marks a Java class as a Spring bean/component.

    **Easy to Remember:** Declares a Spring bean.

16. ### @Autowired
    **Answer:** Used for automatic dependency injection.

    **Easy to Remember:** Auto-injects dependencies.

17. ### Difference Between @Controller, @Component, @Repository, and @Service
    **Answer:**
    - **@Controller:** Handles web requests.
    - **@Component:** General-purpose Spring bean.
    - **@Repository:** Data access object (DAO) support.
    - **@Service:** Business service layer.

    **Easy to Remember:** Different roles for different layers.

18. ### Default Scope of a Bean
    **Answer:** Singleton.

    **Easy to Remember:** Default is singleton.

19. ### Are Spring Beans Thread Safe?
    **Answer:** No, singleton beans are not thread-safe by default.

    **Easy to Remember:** Singleton beans are not thread-safe.

20. ### Other Scopes Available
    **Answer:** Prototype, Request, Session, GlobalSession, Application, WebSocket.

    **Easy to Remember:** Multiple scopes beyond singleton.

21. ### Spring’s Singleton Bean vs. Gang of Four Singleton Pattern
    **Answer:** Spring singleton beans are scoped per Spring container, while GoF Singleton Pattern ensures a class has only one instance in the JVM.

    **Easy to Remember:** Spring singleton is per container, GoF is per JVM.

22. ### Types of Dependency Injections
    **Answer:** Constructor Injection, Setter Injection, Field Injection.

    **Easy to Remember:** Three ways: constructor, setter, field.

23. ### Setter Injection
    **Answer:** Dependency is injected through a setter method.

    **Easy to Remember:** Set dependency using a method.

24. ### Constructor Injection
    **Answer:** Dependency is injected through the constructor.

    **Easy to Remember:** Provide dependency via constructor.

25. ### Choosing Between Setter and Constructor Injections
    **Answer:** Use constructor injection for mandatory dependencies and setter injection for optional ones.

    **Easy to Remember:** Constructor for mandatory, setter for optional.

26. ### Create Application Contexts for Spring
    **Answer:** XML-based, Annotation-based, Java-based configurations.

    **Easy to Remember:** XML, annotations, or Java.

27. ### Difference Between XML and Java Configurations for Spring
    **Answer:** XML is declarative and externalized; Java is type-safe and supports refactoring.

    **Easy to Remember:** XML for external, Java for type safety.

28. ### Choosing Between XML and Java Configurations for Spring
    **Answer:** Use Java for type safety and ease of refactoring; XML for separation of configuration.

    **Easy to Remember:** Java for type safety, XML for separation.

29. ### Spring Autowiring
    **Answer:** Spring automatically injects dependencies using annotations like `@Autowired`.

    **Easy to Remember:** Automatic dependency injection.

30. ### Different Kinds of Matching Used by Spring for Autowiring
    **Answer:** By type, by name, by qualifier.

    **Easy to Remember:** Match by type, name, or qualifier.

31. ### Debug Problems with Spring Framework
    **Answer:** Use logging, check configurations, use Spring’s debug features.

    **Easy to Remember:** Log, check configs, debug tools.

32. ### Solve NoUniqueBeanDefinitionException
    **Answer:** Use `@Primary` or `@Qualifier` to specify which bean to use.

    **Easy to Remember:** Specify bean with `@Primary` or `@Qualifier`.

33. ### Solve NoSuchBeanDefinitionException
    **Answer:** Ensure bean definition exists and is correctly annotated or configured.

    **Easy to Remember:** Ensure correct bean definition.

34. ### @Primary
    **Answer:** Marks a bean as the primary candidate for autowiring.

    **Easy to Remember:** Primary candidate for injection.

35. ### @Qualifier
    **Answer:** Specifies the exact bean to autowire when multiple candidates exist.

    **Easy to Remember:** Specify exact bean.

36. ### CDI (Contexts and Dependency Injection)
    **Answer:** A set of services for Java that supports dependency injection and contextual lifecycle management.

    **Easy to Remember:** Java DI framework.

37. ### Does Spring Support CDI?
    **Answer:** Yes, Spring supports CDI annotations and integrates with CDI.

    **Easy to Remember:** Spring supports CDI.

38. ### Recommend CDI or Spring Annotations
    **Answer:** Use Spring annotations for full Spring features; use CDI for Java EE compatibility.

    **Easy to Remember:** Spring for full features, CDI for Java EE.

39. ### Major Features in Different Versions of Spring
    **Answer:** New features and improvements in each release, such as annotation-based configurations, improved dependency injection, new modules.

    **Easy to Remember:** Each release adds new features and improvements.

40. ### New Features in Spring Framework 4.0
    **Answer:** Java 8 support, WebSocket support, annotation enhancements.

    **Easy to Remember:** Java 8, WebSocket, annotations.

41. ### New Features in Spring Framework 5.0
    **Answer:** Reactive programming support, Java 9 support, Kotlin support.

    **Easy to Remember:** Reactive, Java 9, Kotlin.

42. ### Important Spring Modules
    **Answer:** Core, AOP, Data Access, Web, Messaging, Test.

    **Easy to Remember:** Core, AOP, Data, Web, Messaging, Test.

43. ### Important Spring Projects
    **Answer:** Spring Boot, Spring Cloud, Spring Data, Spring Security, Spring Batch.

    **Easy to Remember:** Boot, Cloud, Data, Security, Batch.

44. ### Ensuring Single Version of All Spring Related Dependencies
    **Answer:** Use Spring Boot’s dependency management.

    **Easy to Remember:** Spring Boot dependency management.

45. ### Design Patterns Used in Spring Framework
    **Answer:** Singleton, Factory, Proxy, Template, Observer, Dependency Injection.

    **Easy to Remember:** Singleton

, Factory, Proxy, Template, Observer, DI.

46. ### Thoughts on Spring Framework
    **Answer:** Spring simplifies Java development with comprehensive infrastructure support for enterprise applications.

    **Easy to Remember:** Simplifies enterprise Java.

47. ### Why is Spring Popular?
    **Answer:** Versatility, extensive ecosystem, strong community support, robust documentation.

    **Easy to Remember:** Versatile, large ecosystem, strong community.

48. ### Big Picture of the Spring Framework
    **Answer:** A comprehensive framework providing support for various enterprise-level functionalities like DI, AOP, MVC, data access, and more.

    **Easy to Remember:** Comprehensive enterprise framework.

49. ### Spring MVC
    **Answer:** A module in Spring for building web applications, providing a model-view-controller architecture.

    **Easy to Remember:** MVC architecture for web apps.