### What is Spring Boot?

**Definition:**
- **Spring Boot:** Spring Boot is a framework built on top of the Spring Framework, designed to simplify the development of Spring-based applications by providing default configurations, embedded servers, and a suite of tools for rapid application development.

### What are the Important Goals of Spring Boot?

**Goals:**
- **Simplification:** Reduce the complexity of configuring Spring applications.
- **Convention over Configuration:** Provide sensible defaults to minimize manual setup.
- **Embedded Servers:** Enable applications to run without external server dependencies.
- **Production-Ready Features:** Provide built-in tools for monitoring, health checks, and configuration.

### What are the Important Features of Spring Boot?

**Features:**
- **Auto Configuration:** Automatically configures Spring application based on dependencies.
- **Embedded Servers:** Support for embedded servers like Tomcat, Jetty, and Undertow.
- **Starter Projects:** Pre-configured dependencies for specific functionalities.
- **Spring Boot Actuator:** Tools for monitoring and managing applications.
- **Externalized Configuration:** Supports external configuration via properties or YAML files.

### Compare Spring Boot vs. Spring

**Comparison:**
- **Spring Boot:** Focuses on rapid application development with minimal configuration. It includes embedded servers and auto-configuration.
- **Spring:** A comprehensive framework for enterprise Java applications, requiring extensive configuration.

### Compare Spring Boot vs. Spring MVC

**Comparison:**
- **Spring Boot:** A wrapper around the Spring Framework that simplifies the setup process, providing auto-configuration and embedded servers.
- **Spring MVC:** A part of the Spring Framework focused on building web applications using the Model-View-Controller pattern.

### What is the Importance of @SpringBootApplication?

**Importance:**
- **@SpringBootApplication:** A convenience annotation that combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`, simplifying the setup of a Spring Boot application.

### What is Auto Configuration?

**Definition:**
- **Auto Configuration:** A Spring Boot feature that automatically configures your application based on the dependencies on the classpath.

### How Can We Find More Information About Auto Configuration?

**Information Source:**
- **Spring Boot Documentation:** Check the official documentation or use the `spring-boot-autoconfigure` jar to explore configuration classes.

### What is an Embedded Server? Why is it Important?

**Definition & Importance:**
- **Embedded Server:** A server (e.g., Tomcat, Jetty) embedded within the application, allowing it to run independently without relying on external servers. This simplifies deployment and testing.

### What is the Default Embedded Server with Spring Boot?

**Default Server:**
- **Tomcat:** The default embedded server in Spring Boot.

### What are the Other Embedded Servers Supported by Spring Boot?

**Supported Servers:**
- **Jetty**
- **Undertow**

### What are Starter Projects?

**Definition:**
- **Starter Projects:** Pre-configured dependency descriptors to simplify the setup of specific functionalities in Spring Boot.

### Can You Give Examples of Important Starter Projects?

**Examples:**
- **spring-boot-starter-web:** For building web applications.
- **spring-boot-starter-data-jpa:** For JPA and database access.
- **spring-boot-starter-security:** For adding security features.

### What is Starter Parent?

**Definition:**
- **Starter Parent:** A special parent project in Spring Boot that provides default configurations for plugins, dependency management, and other build configurations.

### What are the Different Things that are Defined in Starter Parent?

**Defined Aspects:**
- **Default Java Version**
- **Dependency Management**
- **Plugin Management**
- **Common Maven/Gradle configurations**

### How Does Spring Boot Enforce Common Dependency Management for All Its Starter Projects?

**Enforcement:**
- **Dependency Management:** Spring Boot's `starter-parent` defines a common set of dependencies, versions, and configurations, ensuring consistency across projects.

### What is Spring Initializr?

**Definition:**
- **Spring Initializr:** A web-based tool that provides a quick way to generate a new Spring Boot project with a custom set of dependencies.

### What is application.properties?

**Definition:**
- **application.properties:** A configuration file used in Spring Boot to define application-level settings, such as database connections, server ports, and more.

### What are Some of the Important Things that Can be Customized in application.properties?

**Customizations:**
- **Server Port:** `server.port`
- **Database URL:** `spring.datasource.url`
- **Logging Level:** `logging.level`

### How Do You Externalize Configuration Using Spring Boot?

**Externalization:**
- **External Configuration:** Spring Boot allows external configuration through properties files, YAML files, environment variables, and command-line arguments.

### How Can You Add Custom Application Properties Using Spring Boot?

**Custom Properties:**
- **Custom Properties:** Define your own properties in `application.properties` and access them using `@Value` or `@ConfigurationProperties` in your code.

### What is @ConfigurationProperties?

**Definition:**
- **@ConfigurationProperties:** An annotation that binds external properties (e.g., from `application.properties`) to a Java object, making it easier to manage configurations.

### What is a Profile?

**Definition:**
- **Profile:** A Spring feature that allows you to define different beans or configurations for different environments (e.g., development, production).

### How Do You Define Beans for a Specific Profile?

**Bean Definition:**
- **@Profile:** Use the `@Profile` annotation on bean definitions to specify which profile they belong to.

### How Do You Create Application Configuration for a Specific Profile?

**Profile Configuration:**
- **Profile-Specific Files:** Use `application-{profile}.properties` or `application-{profile}.yml` to define profile-specific configurations.

### How Do You Have Different Configuration for Different Environments?

**Environment Configuration:**
- **Profiles:** Define different profiles for each environment and specify the active profile using `spring.profiles.active`.

### What is Spring Boot Actuator?

**Definition:**
- **Spring Boot Actuator:** A Spring Boot module that provides production-ready features, such as monitoring, metrics, and health checks.

### How Do You Monitor Web Services Using Spring Boot Actuator?

**Monitoring:**
- **Actuator Endpoints:** Enable and access Actuator endpoints (e.g., `/actuator/health`) to monitor the status and metrics of your web services.

### How Do You Find More Information About Your Application Environment Using Spring Boot?

**Environment Info:**
- **Actuator:** Use the `/actuator/env` endpoint to access detailed information about your application's environment and configuration.

### What is a CommandLineRunner?

**Definition:**
- **CommandLineRunner:** An interface in Spring Boot used to execute code after the Spring Boot application has started. It is typically used to run startup logic.