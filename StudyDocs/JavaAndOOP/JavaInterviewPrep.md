### Java Basics

#### 1. What is JVM? Why is Java called the Platform Independent Programming Language?
The Java Virtual Machine (JVM) executes Java bytecode. Java files are converted to bytecode, which the JVM executes. JVMs are developed according to platform requirements, but the bytecode can run on any JVM or platform, making Java platform-independent.

#### 2. What is the Difference between JDK and JRE?
- **Java Runtime Environment (JRE):** Includes the JVM where Java programs are executed and browser plugins for applet execution.
- **Java Development Kit (JDK):** A comprehensive software development kit for Java, including the JRE, compilers, and tools like JavaDoc and Java Debugger, for developing, compiling, and executing Java applications.

#### 3. What does the “static” keyword mean? Can you override private or static methods in Java?
- **Static Keyword:** Allows access to variables or methods without instantiating a class.
- **Overriding:** Static methods cannot be overridden because they are resolved at compile time, while method overriding occurs at runtime.

#### 4. Can you access non-static variables in a static context?
No, static variables belong to the class and not to any instance. Accessing non-static variables from a static context results in a compile-time error because non-static variables are not associated with any instance yet.

### Wrapper Classes in Java

#### 5. Wrapper Classes in Java
Wrapper classes in Java allow primitive data types (int, char, etc.) to be used as objects.

#### 6. Wrapper Class Creation:
- **Using Constructors:** Every call to a constructor creates a new object.
    ```java
    Integer obj1 = new Integer(10); // Creates a new Integer object
    ```
- **Using Factory Methods:** The `valueOf` method may return a cached object, improving performance.
    ```java
    Integer obj2 = Integer.valueOf(10); // May return a cached instance
    ```

#### 7. What is Auto-boxing and Unboxing?
- **Auto-boxing:** Automatic conversion between primitive types and their corresponding wrapper classes.
- **Unboxing:** Conversion from wrapper classes to primitive types.

### Casting

#### 8. What is Casting?
Casting is the process of converting a variable from one type to another. It can be implicit or explicit.

#### 9. Implicit Casting/Widening/Up Casting
Implicit casting is the automatic conversion of a smaller data type to a larger data type, which is safe and does not result in data loss.
```java
int intVal = 100;
long longVal = intVal; // Implicit casting from int to long
```

#### 10. Explicit Casting/Narrowing/Down Casting
Explicit casting is the manual conversion from a larger data type to a smaller one, which can result in data loss.
```java
long longVal = 100L;
int intVal = (int) longVal; // Explicit casting from long to int
```

#### 11. Are all Strings immutable?
Yes, all `String` objects are immutable. Once created, a `String` object’s value cannot be changed; any modification results in a new `String` object.

### String Handling

#### 12. Where are String values stored in memory?
String values are stored in the String Pool within the heap memory. Java checks this pool to reuse existing strings or create new ones.

#### 13. Why should you be careful about the String concatenation (`+`) operator in loops?
Using `+` for String concatenation in loops is inefficient as each concatenation creates a new `String` object, leading to multiple temporary objects and high memory overhead.

#### 14. How do you solve the String concatenation problem?
Use `StringBuilder` or `StringBuffer` for efficient string concatenation in loops. These classes are mutable and designed to avoid creating multiple temporary objects.

### StringBuffer vs. StringBuilder

#### 15. Differences Between String and StringBuffer
- **String:**
  - Immutable: Value cannot be changed once created.
  - Thread-safe: Naturally thread-safe due to immutability.
  - Performance: Slower for concatenation due to immutability.

- **StringBuffer:**
  - Mutable: Value can be changed.
  - Thread-safe: Methods are synchronized.
  - Performance: Slower than `StringBuilder` due to synchronization but faster than `String` for concatenation.

#### 16. Differences Between StringBuilder and StringBuffer
- **StringBuilder:**
  - Mutable: Value can be changed.
  - Not thread-safe: Not synchronized.
  - Performance: Faster than `StringBuffer` due to lack of synchronization overhead.

- **StringBuffer:**
  - Mutable: Value can be changed.
  - Thread-safe: Synchronized methods make it thread-safe.
  - Performance: Slower than `StringBuilder` due to synchronization.

### Utility Methods in the String Class

#### 17. Examples of Different Utility Methods in the String Class:
1. **`length()`**
   - Returns the length of the string.
   ```java
   String str = "Hello";
   int length = str.length(); // 5
   ```

2. **`charAt(int index)`**
   - Returns the character at the specified index.
   ```java
   char ch = str.charAt(1); // 'e'
   ```

3. **`substring(int beginIndex, int endIndex)`**
   - Returns a new string that is a substring of this string.
   ```java
   String sub = str.substring(1, 4); // "ell"
   ```

4. **`indexOf(String str)`**
   - Returns the index of the first occurrence of the specified substring.
   ```java
   int index = str.indexOf("l"); // 2
   ```

5. **`equals(Object anObject)`**
   - Compares this string to the specified object.
   ```java
   boolean isEqual = str.equals("Hello"); // true
   ```

6. **`toLowerCase()`**
   - Converts all characters in the string to lowercase.
   ```java
   String lower = str.toLowerCase(); // "hello"
   ```

7. **`toUpperCase()`**
   - Converts all characters in the string to uppercase.
   ```java
   String upper = str.toUpperCase(); // "HELLO"
   ```

8. **`trim()`**
   - Returns a copy of the string with leading and trailing whitespace removed.
   ```java
   String trimmed = "  Hello  ".trim(); // "Hello"
   ```

9. **`replace(char oldChar, char newChar)`**
   - Returns a new string with all occurrences of `oldChar` replaced by `newChar`.
   ```java
   String replaced = str.replace('l', 'p'); // "Heppo"
   ```

10. **`split(String regex)`**
    - Splits the string around matches of the given regular expression.
    ```java
    String[] parts = str.split("l"); // ["He", "", "o"]
    ```