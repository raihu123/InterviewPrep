### Exception Handling in Java

#### 1. What design pattern is used to implement exception handling features in most languages?
**Answer:** The **Chain of Responsibility** design pattern is often used to implement exception handling features. This pattern allows multiple handlers to process an exception in a chain until it is handled.

**Easy to Remember:** Exception handling often uses the Chain of Responsibility pattern, passing exceptions along a chain until handled.

#### 2. What is the need for the `finally` block?
**Answer:** The `finally` block is used to execute important code such as resource cleanup, regardless of whether an exception is thrown or not. It ensures that resources like files, database connections, or network connections are properly closed.

**Easy to Remember:** `finally` is for cleanup tasks that must run no matter what.

#### 3. In what scenarios is code in `finally` not executed?
**Answer:** The `finally` block is not executed in the following scenarios:
- If the JVM exits due to a call to `System.exit()`.
- If the JVM crashes.
- If a `Thread` is interrupted or killed.

**Easy to Remember:** `finally` is skipped if the JVM exits or crashes.

#### 4. Will `finally` be executed in the program below?
```java
public class Example {
    public static void main(String[] args) {
        try {
            System.out.println("Try block");
            return;
        } finally {
            System.out.println("Finally block");
        }
    }
}
```
**Answer:** Yes, the `finally` block will be executed and the output will be:
```
Try block
Finally block
```

**Explanation:** The `finally` block is executed even if there is a `return` statement in the `try` block.

#### 5. Is `try` without a `catch` allowed?
**Answer:** Yes, `try` without a `catch` is allowed as long as it has a `finally` block.

**Example:**
```java
try {
    // code
} finally {
    // cleanup code
}
```

**Easy to Remember:** `try` must be paired with either `catch` or `finally`.

#### 6. Is `try` without `catch` and `finally` allowed?
**Answer:** No, `try` must be followed by either `catch` or `finally` (or both).

**Easy to Remember:** `try` cannot stand alone; it needs `catch` or `finally`.

#### 7. Can you explain the hierarchy of exception handling classes?
**Answer:** The exception handling hierarchy in Java is as follows:
- `Throwable`
  - `Error`
    - `LinkageError`
    - `VirtualMachineError`
    - ... (other `Error` subclasses)
  - `Exception`
    - `RuntimeException`
      - `ArithmeticException`
      - `NullPointerException`
      - ... (other `RuntimeException` subclasses)
    - `IOException`
    - `SQLException`
    - ... (other checked exceptions)

**Easy to Remember:** At the top is `Throwable`, which branches into `Error` and `Exception`, with `Exception` further divided into `RuntimeException` (unchecked) and other checked exceptions.

#### 8. What is the difference between error and exception?
**Answer:**
- **Error:** Represents serious issues that a reasonable application should not try to catch but you logically you can catch it (e.g., `OutOfMemoryError`, `StackOverflowError`).
- **Exception:** Represents conditions that a reasonable application might want to catch and handle (e.g., `IOException`, `SQLException`).

**Easy to Remember:** Errors are serious and usually fatal; exceptions are manageable issues.

#### 9. What is the difference between checked exceptions and unchecked exceptions?
**Answer:**
- **Checked Exceptions:** Must be declared in the method signature using `throws` or handled with a `try-catch` block. They are checked at compile-time (e.g., `IOException`, `SQLException`).
- **Unchecked Exceptions:** Do not need to be declared or caught. They are checked at runtime (e.g., `NullPointerException`, `ArithmeticException`). Typically Unchecked Exception are the child of RuntimeException

**Easy to Remember:** Checked exceptions are checked at compile-time; unchecked at runtime.

#### 10. How do you throw an exception from a method?
**Answer:** Use the `throw` keyword followed by an instance of `Throwable`.

**Example:**
```java
public void myMethod() throws Exception {
    throw new Exception("An error occurred");
}
```

**Easy to Remember:** Use `throw new Exception()` to throw an exception.

#### 11. What happens when you throw a checked exception from a method?
**Answer:** The method must declare the exception in its `throws` clause, and the caller must handle or declare the exception.

**Example:**
```java
public void myMethod() throws IOException {
    throw new IOException("IO error");
}
```

**Easy to Remember:** Declare checked exceptions in the method signature with `throws`.

#### 12. What are the options you have to eliminate compilation errors when handling checked exceptions?
**Answer:**
1. Handle the exception with a `try-catch` block.
2. Declare the exception using the `throws` keyword in the method signature.

**Example:**
```java
// Option 1: Handle with try-catch
public void myMethod() {
    try {
        // code that may throw IOException
    } catch (IOException e) {
        e.printStackTrace();
    }
}

// Option 2: Declare with throws
public void myMethod() throws IOException {
    // code that may throw IOException
}
```

**Easy to Remember:** Handle with `try-catch` or declare with `throws`.

#### 13. How do you create a custom exception?
**Answer:** Extend the `Exception` class (for a checked exception) or `RuntimeException` class (for an unchecked exception).

**Example:**
```java
public class MyCustomException extends Exception {
    public MyCustomException(String message) {
        super(message);
    }
}
```

**Easy to Remember:** Extend `Exception` for checked, `RuntimeException` for unchecked custom exceptions.

#### 14. How do you handle multiple exception types with the same exception handling block?
**Answer:** Use a multi-catch block.

**Example:**
```java
try {
    // code that may throw exceptions
} catch (IOException | SQLException e) {
    e.printStackTrace();
}
```

**Easy to Remember:** Use `catch(ExceptionType1 | ExceptionType2 e)` for multiple exceptions.

#### 15. Can you explain about try-with-resources?
**Answer:** The try-with-resources statement ensures that each resource is closed at the end of the statement. Resources that are declared within the parentheses of the `try` statement must implement the `AutoCloseable` interface.

**Example:**
```java
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    // Use the resource
} catch (IOException e) {
    e.printStackTrace();
}
```

**Easy to Remember:** `try-with-resources` automatically closes resources.

#### 16. How does try-with-resources work?
**Answer:** The resources declared in the `try` block are automatically closed at the end of the block. The `close()` method is called on each resource, ensuring proper cleanup.

**Easy to Remember:** Resources in `try()` are auto-closed after the block.

#### 17. Can you explain a few exception handling best practices?
**Answer:**
1. **Catch Specific Exceptions:** Avoid catching generic exceptions; catch specific ones to handle errors precisely.
2. **Log Exceptions:** Log exceptions for debugging and record-keeping.
3. **Do Not Suppress Exceptions:** Do not catch an exception without handling it properly.
4. **Use Finally for Cleanup:** Use the `finally` block to release resources.
5. **Provide Meaningful Messages:** When throwing exceptions, provide detailed messages to understand the error context.
6. **Document Exceptions:** Use JavaDoc to document the exceptions a method might throw.

**Easy to Remember:** Be specific, log errors, don't suppress, clean up, explain, and document.

#### 18. What Will Happen to the Exception Object After Exception Handling?

**Answer:** After exception handling, the `Exception` object is eligible for garbage collection if there are no more references to it. Once the `catch` block completes, the `Exception` object is no longer in use, provided it is not stored or referenced elsewhere in the code. The Java garbage collector will eventually reclaim the memory used by the `Exception` object.

**Easy to Remember:** After handling an exception, the `Exception` object is usually discarded and may be collected by the garbage collector if not referenced elsewhere.

#### 19. How Does the `finally` Block Differ from the `finalize()` Method?

**Answer:**

- **`finally` Block:**
  - **Purpose:** Used for code that must always be executed after a `try` block, regardless of whether an exception is thrown or not. Commonly used for resource cleanup like closing files or releasing resources.
  - **Execution:** Executes after the `try` block and any `catch` blocks. It always runs unless the JVM exits or crashes.
  - **Syntax:** Part of exception handling.
  
  **Example:**
  ```java
  try {
      // code that may throw an exception
  } finally {
      // cleanup code, always executed
  }
  ```

- **`finalize()` Method:**
  - **Purpose:** Used for cleanup before an object is garbage collected. It allows an object to perform cleanup before being reclaimed by the garbage collector.
  - **Execution:** Called by the garbage collector on an object when garbage collection determines that there are no more references to the object.
  - **Syntax:** A method of the `Object` class, overridden in a class to define custom finalization code.
  
  **Example:**
  ```java
  @Override
  protected void finalize() throws Throwable {
      try {
          // cleanup code before garbage collection
      } finally {
          super.finalize(); // Always call the superclass finalize
      }
  }
  ```

**Easy to Remember:**

- **`finally`**: Ensures code runs after `try`/`catch` for resource cleanup.
- **`finalize()`**: Runs before an object is garbage collected for last-minute cleanup.

In summary, `finally` is part of exception handling to ensure certain code runs regardless of exceptions, while `finalize()` is a method called by the garbage collector to clean up resources before an object is destroyed.


### Exception Handling in Inheritance

#### Case 1: SuperClass declares an exception and SubClass declares exceptions other than the child exception of the SuperClass declared Exception.
- **Explanation:** This is not allowed. The subclass method cannot declare a broader or completely different exception than the superclass method.
- **Easy to Remember:** SubClass can't throw a new or broader exception.

#### Case 2: SuperClass declares an exception and SubClass declares a child exception of the SuperClass declared Exception.
- **Explanation:** This is allowed. The subclass can declare an exception that is a subclass of the exception declared by the superclass.
- **Easy to Remember:** SubClass can throw a more specific (child) exception.

#### Case 3: SuperClass declares an exception and SubClass declares without exception.
- **Explanation:** This is allowed. The subclass can choose not to declare any exception even if the superclass does.
- **Easy to Remember:** SubClass can choose to throw no exception.

#### Case 4: SuperClass doesn’t declare any exception and SubClass declares a checked exception.
- **Explanation:** This is not allowed. The subclass cannot declare a checked exception if the superclass method does not declare any exception.
- **Easy to Remember:** SubClass can't add checked exceptions if SuperClass has none.

#### Case 5: SuperClass doesn’t declare any exception and SubClass declares an unchecked exception.
- **Explanation:** This is allowed. The subclass can declare unchecked (runtime) exceptions even if the superclass does not declare any exceptions.
- **Easy to Remember:** SubClass can add unchecked exceptions freely.

### Summary

1. **SuperClass declares an exception:** 
   - SubClass can't throw new or broader exceptions.
   - SubClass can throw child exceptions.
   - SubClass can choose to throw no exceptions.

2. **SuperClass doesn’t declare any exception:** 
   - SubClass can't throw checked exceptions.
   - SubClass can throw unchecked exceptions.