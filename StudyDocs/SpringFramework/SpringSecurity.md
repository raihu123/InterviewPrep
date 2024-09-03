### Key Features of Spring Security

1. **Comprehensive Authentication and Authorization**: Supports multiple authentication methods (like form-based, LDAP, OAuth2) and role-based access control.
2. **CSRF Protection**: Protects against Cross-Site Request Forgery attacks.
3. **Session Management**: Handles session fixation, concurrent session control, etc.
4. **Integration with Servlet API**: Works seamlessly with Java Servlet API.
5. **Password Storage**: Provides hashing algorithms for secure password storage.
6. **Security Filters**: Uses a customizable filter chain for request filtering and security processing.
7. **Declarative Security**: Configurable via XML, Java annotations, and code.

### Difference Between Authentication and Authorization

- **Authentication**: Verifies the identity of a user (e.g., username and password).
- **Authorization**: Determines if the authenticated user has permission to access specific resources or perform certain actions.

### How to Configure Authentication in Spring Security

Authentication can be configured using `SecurityConfigurerAdapter`:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication()
            .withUser("user").password("{noop}password").roles("USER")
            .and()
            .withUser("admin").password("{noop}admin").roles("ADMIN");
    }
}
```

- This example configures in-memory authentication with two users.

### How to Configure Authorization in Spring Security

Authorization is configured by overriding the `configure(HttpSecurity http)` method:

```java
@Override
protected void configure(HttpSecurity http) throws Exception {
    http.authorizeRequests()
        .antMatchers("/admin/**").hasRole("ADMIN")
        .antMatchers("/user/**").hasAnyRole("USER", "ADMIN")
        .antMatchers("/").permitAll()
        .and().formLogin();
}
```

- This specifies that only users with the "ADMIN" role can access the `/admin/**` endpoint, while any authenticated user can access `/user/**`.

### Explain Basic Authentication in Spring Security

Basic Authentication involves sending the username and password encoded in the HTTP header. It can be enabled with:

```java
http.authorizeRequests()
    .anyRequest().authenticated()
    .and()
    .httpBasic();
```

### How to Enable and Disable CSRF in Spring Security

- **Enable CSRF** (default behavior):

```java
http.csrf().enable();
```

- **Disable CSRF**:

```java
http.csrf().disable();
```

- CSRF protection should be disabled for stateless APIs (like RESTful services).

### What is a Filter Chain in Spring Security?

The **Filter Chain** is a series of filters that process incoming HTTP requests to apply security checks, authentication, and authorization. Examples include `UsernamePasswordAuthenticationFilter`, `CsrfFilter`, and `ExceptionTranslationFilter`.

### When to Use `antMatcher()` in Spring Security?

- `antMatcher()` is used to match specific URL patterns for applying security rules. For example:

```java
http.antMatcher("/admin/**").authorizeRequests().anyRequest().hasRole("ADMIN");
```

### How to Implement Spring Security in a Simple Spring Boot Application?

1. Add the Spring Security dependency to `pom.xml` or `build.gradle`.
2. Create a `SecurityConfig` class extending `WebSecurityConfigurerAdapter`.
3. Override the `configure` methods to set up authentication and authorization.
4. Secure the endpoints as needed.

### How to Configure Spring Security in a Spring MVC Application?

1. Add Spring Security dependencies to your project.
2. Create a `SecurityConfig` class and annotate it with `@Configuration` and `@EnableWebSecurity`.
3. Set up authentication and authorization rules using `configure(HttpSecurity http)` and `configure(AuthenticationManagerBuilder auth)` methods.

### How to Deny Access to All URLs in Spring Security?

```java
@Override
protected void configure(HttpSecurity http) throws Exception {
    http.authorizeRequests().anyRequest().denyAll();
}
```

### How to Get the Current Logged-in User Details in Spring Security?

Use `SecurityContextHolder`:

```java
Authentication auth = SecurityContextHolder.getContext().getAuthentication();
String username = auth.getName();
```

### What is JWT in Spring Security?

**JWT (JSON Web Token)** is a token-based authentication mechanism that allows secure, stateless communication between client and server. It is used to verify the identity of a user.

### What is OAuth and OAuth2 in Spring Security?

- **OAuth** is an authorization framework that allows third-party applications to access user resources without exposing credentials.
- **OAuth2** is the newer, more secure version with more features, supported by Spring Security for client and resource server implementations.

### What is Keycloak and Explain the Integration of Keycloak with Spring Security?

- **Keycloak** is an open-source identity and access management solution. It provides SSO (Single Sign-On) and supports standard protocols like OAuth2 and SAML.
- To integrate with Spring Security:
  1. Add Keycloak Spring Boot adapter dependencies.
  2. Configure `KeycloakSpringBootConfigResolver` and `KeycloakConfigResolver` beans.
  3. Secure endpoints by defining roles and scopes in `application.properties`.

### What is the Role of an AuthenticationProvider in Spring Security?

An **AuthenticationProvider** processes the authentication request. It implements the `authenticate()` method to verify credentials and provide authentication objects for users.

### How to Secure an Endpoint in Spring Security?

Use `@PreAuthorize` or configure in `SecurityConfig`:

```java
@PreAuthorize("hasRole('ADMIN')")
@GetMapping("/admin")
public String adminPage() {
    return "Admin Page";
}
```

### Secure Specific Endpoints

Specify security rules for specific endpoints in `configure(HttpSecurity http)`:

```java
http.authorizeRequests().antMatchers("/admin/**").hasRole("ADMIN");
```

### Explain `UserDetailsService` and `UserDetails` in Spring Security

- **`UserDetailsService`**: An interface used to retrieve user details like username, password, and roles from a data source.
- **`UserDetails`**: Represents a user in Spring Security, containing necessary information (username, password, roles, etc.).

### What is Method-Level Security in Spring Security?

**Method-Level Security** secures individual methods using annotations like `@Secured`, `@PreAuthorize`, and `@PostAuthorize`.

### Difference Between `hasRole()` and `hasAuthority()`

- **`hasRole()`**: Checks for roles prefixed with "ROLE_".
- **`hasAuthority()`**: Checks for exact authority or permission names.

### What is `SessionManagement` in Spring Security?

Manages user sessions, providing features like concurrent session control, session timeout, and prevention of session fixation attacks.

### What is `DelegatingFilterProxy` in Spring Security?

A servlet filter that delegates the request to a Spring-managed bean that implements the `Filter` interface.

### How to Implement Two-Factor Authentication (2FA) in Spring Security?

1. Implement the first factor (e.g., username/password).
2. Generate a token or OTP as the second factor.
3. Verify the second factor before allowing access.

### Explain Hashing in Spring Security

**Hashing** is the process of converting passwords into a fixed-size string of characters. Spring Security supports secure hashing algorithms like BCrypt.

### How Spring Security Handles User Authentication?

Spring Security uses `AuthenticationManager` to process authentication, using a chain of `AuthenticationProvider`s to validate credentials.

### Potential Web Application Vulnerabilities and How Spring Security Mitigates Them

1. **Cross-Site Scripting (XSS)**: Encodes output to prevent script execution.
2. **CSRF Attacks**: Provides built-in CSRF protection.
3. **Session Fixation**: Prevents session fixation attacks by regenerating session IDs.
4. **Man-in-the-Middle (MITM) Attacks**: Supports HTTPS and TLS configuration.

### How to Implement Spring Security with In-Memory User Storage

```java
@Override
protected void configure(AuthenticationManagerBuilder auth) throws Exception {
    auth.inMemoryAuthentication()
        .withUser("user").password("{noop}password").roles("USER");
}
```

### Explain Salting and Its Usage

**Salting** is adding a unique, random string to each password before hashing to protect against rainbow table attacks. Spring Security's `BCryptPasswordEncoder` handles salting automatically.