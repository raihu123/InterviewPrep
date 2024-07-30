#### 1. What is Functional Programming?
**Answer:** Functional programming is a programming paradigm where programs are constructed by applying and composing functions. It emphasizes immutability, first-class functions, and declarative code.

**Easy to Remember:** Functional programming builds programs with functions and avoids changing state.

#### 2. Example of Functional Programming
**Example:** Using Java Streams API to filter and sum a list of integers.
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int sum = numbers.stream()
                 .filter(n -> n % 2 == 0)
                 .mapToInt(Integer::intValue)
                 .sum();
```
**Easy to Remember:** Use Streams API to process collections with functions like filter and map.

#### 3. What is a Stream?
**Answer:** A stream is a sequence of elements that supports various methods to perform computations on the elements, such as filtering, mapping, and reducing. Streams do not store elements; they compute them on demand.

**Easy to Remember:** Streams process data in sequences without storing them.

#### 4. Streams Example
**Example:** Filtering and printing even numbers from a list.
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.stream()
       .filter(n -> n % 2 == 0)
       .forEach(System.out::println);
```
**Easy to Remember:** Use `stream()`, `filter()`, and `forEach()` to process data.

#### 5. Intermediate Operations in Streams
**Answer:** Intermediate operations transform a stream into another stream. They are lazy and only executed when a terminal operation is invoked.
- **Examples:** `filter()`, `map()`, `sorted()`

**Easy to Remember:** Intermediate operations like `filter()` and `map()` transform streams and are lazy.

#### 6. Terminal Operations in Streams
**Answer:** Terminal operations produce a result or side-effect and mark the end of the stream processing.
- **Examples:** `forEach()`, `collect()`, `reduce()`

**Easy to Remember:** Terminal operations like `forEach()` and `collect()` finalize stream processing.

#### 7. What are Method References?
**Answer:** Method references are shorthand for lambda expressions that call a specific method. They use the `::` operator.
- **Example:** `String::toUpperCase`

**Easy to Remember:** Method references like `ClassName::methodName` simplify calling methods.

#### 8. What are Lambda Expressions?
**Answer:** Lambda expressions provide a concise way to represent anonymous functions (function literals). They have a simple syntax: `(parameters) -> expression`.

**Easy to Remember:** Lambda expressions are anonymous functions using `->`.

#### 9. Lambda Expression Example
**Example:** Using a lambda to filter a list of strings.
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<String> filteredNames = names.stream()
                                  .filter(name -> name.startsWith("A"))
                                  .collect(Collectors.toList());
```
**Easy to Remember:** Use `(parameters) -> expression` for concise function definitions.

#### 10. Relationship Between Lambda Expressions and Functional Interfaces
**Answer:** A lambda expression can be used to instantiate an interface with a single abstract method, known as a functional interface.
- **Example:** `Runnable` and `Callable` are functional interfaces.

**Easy to Remember:** Lambdas implement single-method interfaces (functional interfaces).

#### 11. What is a Predicate?
**Answer:** A `Predicate` is a functional interface representing a boolean-valued function of one argument.
- **Example:** `Predicate<Integer> isEven = n -> n % 2 == 0;`

**Easy to Remember:** `Predicate` checks conditions with `test()` method.

#### 12. What is the Functional Interface - Function?
**Answer:** `Function<T, R>` is a functional interface representing a function that takes an argument of type T and returns a result of type R.
- **Example:** `Function<String, Integer> lengthFunction = String::length;`

**Easy to Remember:** `Function<T, R>` maps inputs of type T to outputs of type R.

#### 13. What is a Consumer?
**Answer:** `Consumer<T>` is a functional interface representing an operation that takes a single argument and returns no result.
- **Example:** `Consumer<String> printConsumer = System.out::println;`

**Easy to Remember:** `Consumer<T>` performs operations on inputs without returning results.

#### 14. Examples of Functional Interfaces with Multiple Arguments
**Examples:**
- **BiFunction<T, U, R>:** Takes two arguments of types T and U, returns a result of type R.
  ```java
  BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;
  ```
- **BiConsumer<T, U>:** Takes two arguments of types T and U, performs an operation without returning a result.
  ```java
  BiConsumer<String, String> printNames = (firstName, lastName) -> System.out.println(firstName + " " + lastName);
  ```

**Easy to Remember:** `BiFunction` and `BiConsumer` handle two arguments.