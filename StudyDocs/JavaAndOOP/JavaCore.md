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

| Method                            | Description                                                              | Example                                                                                   |
|-----------------------------------|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| **`length()`**                    | Returns the length of the string.                                         | ```java<br>String str = "Hello";<br>int length = str.length(); // 5<br>```                |
| **`charAt(int index)`**           | Returns the character at the specified index.                             | ```java<br>char ch = str.charAt(1); // 'e'<br>```                                         |
| **`substring(int beginIndex, int endIndex)`** | Returns a new string that is a substring of this string.               | ```java<br>String sub = str.substring(1, 4); // "ell"<br>```                              |
| **`indexOf(String str)`**         | Returns the index of the first occurrence of the specified substring.     | ```java<br>int index = str.indexOf("l"); // 2<br>```                                      |
| **`equals(Object anObject)`**     | Compares this string to the specified object.                             | ```java<br>boolean isEqual = str.equals("Hello"); // true<br>```                          |
| **`toLowerCase()`**               | Converts all characters in the string to lowercase.                       | ```java<br>String lower = str.toLowerCase(); // "hello"<br>```                            |
| **`toUpperCase()`**               | Converts all characters in the string to uppercase.                       | ```java<br>String upper = str.toUpperCase(); // "HELLO"<br>```                            |
| **`trim()`**                      | Returns a copy of the string with leading and trailing whitespace removed.| ```java<br>String trimmed = "  Hello  ".trim(); // "Hello"<br>```                         |
| **`replace(char oldChar, char newChar)`** | Returns a new string with all occurrences of `oldChar` replaced by `newChar`. | ```java<br>String replaced = str.replace('l', 'p'); // "Heppo"<br>```                    |
| **`split(String regex)`**         | Splits the string around matches of the given regular expression.         | ```java<br>String[] parts = str.split("l"); // ["He", "", "o"]<br>```                     |


### Access Modifiers in Java

#### 18. What is the default class modifier?
**Definition:** If no access modifier is specified, a class is considered to have default or package-private access. This means the class is only accessible within its own package.

**Easy to Remember:** If you don't write any access modifier, it defaults to package-private.

#### 19. What is the private access modifier?
**Definition:** The `private` access modifier restricts access to members of the class from any other class. These members are only accessible within the class they are declared in.

**Example:**
```java
public class Example {
    private int number; // Only accessible within Example class
}
```

**Easy to Remember:** Private members are like personal secrets; only the owner knows them.

#### 20. What is the default or package access modifier?
**Definition:** The default or package-private access modifier allows access to members from any class within the same package. No keyword is used; it's simply the absence of an explicit modifier.

**Example:**
```java
class Example {
    int number; // Accessible within the same package
}
```

**Easy to Remember:** If you don’t specify an access level, it's package-private by default.

#### 21. What is the protected access modifier?
**Definition:** The `protected` access modifier allows access to members from within the same package and also from subclasses, even if they are in different packages.

**Example:**
```java
public class Example {
    protected int number; // Accessible within the same package and subclasses
}
```

**Easy to Remember:** Protected members are like family secrets; they can be shared with children (subclasses) and relatives (other classes in the package).

#### 22. What is the public access modifier?
**Definition:** The `public` access modifier allows access to members from any other class in any package.

**Example:**
```java
public class Example {
    public int number; // Accessible from any class
}
```

**Easy to Remember:** Public members are like public news; everyone can access them.

### Variable Access by Location

#### 23. What access types of variables can be accessed from a class in the same package?
- Default (package-private)
- Protected
- Public

#### 24. What access types of variables can be accessed from a class in a different package?
- Public

#### 25. What access types of variables can be accessed from a subclass in the same package?
- Default (package-private)
- Protected
- Public

#### 26. What access types of variables can be accessed from a subclass in a different package?
- Protected
- Public

### Final Modifier

#### 27. What is the use of a final modifier on a class?
**Definition:** A class declared as `final` cannot be subclassed. This is used to prevent inheritance.

**Example:**
```java
public final class Example {
    // Cannot be extended
}
```

**Easy to Remember:** Final classes are like sealed boxes; you cannot add anything to them.

#### 28. What is the use of a final modifier on a method?
**Definition:** A method declared as `final` cannot be overridden by subclasses.

**Example:**
```java
public class Example {
    public final void display() {
        // Cannot be overridden
    }
}
```

**Easy to Remember:** Final methods are like final decisions; they cannot be changed.

#### 29. What is a final variable?
**Definition:** A variable declared as `final` cannot be changed once it is initialized.

**Example:**
```java
public class Example {
    public final int number = 10; // Cannot be reassigned
}
```

**Easy to Remember:** Final variables are like constants; their value does not change.

#### 30. What is a final argument?
**Definition:** A method parameter declared as `final` cannot be changed within the method.

**Example:**
```java
public void display(final int number) {
    // number cannot be reassigned
}
```

**Easy to Remember:** Final arguments are like fixed rules; they remain the same within their scope.

### Other Modifiers

#### 31. What happens when a variable is marked as volatile?
**Definition:** A `volatile` variable is a special modifier used in multi-threaded programming. It indicates that the value of the variable can change unexpectedly and ensures that every thread reads the value of the variable directly from the main memory, rather than from a thread-local cache.

**Example:**
```java
public class Example {
    private volatile boolean flag;
}
```

**Easy to Remember:** Volatile variables are like live wires; they can change state at any time.

#### 32. What is a static variable?
**Definition:** A `static` variable belongs to the class rather than to any specific instance. It is shared among all instances of the class.

**Example:**
```java
public class Example {
    public static int count;
}
```
**Easy to Remember:** Static variables are like class-wide announcements; every instance hears the same thing.



#### 33. Guess the output
**Question:** What will be the output of the following code?
```java
public class GuessOutput {
    public static void main(String[] args) {
        int x = 1;
        int y = 1;
        if (x++ > 0 && y++ > 0) {
            x = 10;
        }
        System.out.println("x = " + x + " y = " + y);
    }
}
```
**Answer:** The output will be:
```
x = 10 y = 2
```

**Explanation:** The condition `x++ > 0` evaluates to true (1 > 0), so `x` is incremented to 2. The condition `y++ > 0` also evaluates to true (1 > 0), so `y` is incremented to 2. Since both conditions are true, `x` is set to 10.

#### 34. Guess the output of this switch block
**Question:** What will be the output of the following code?
```java
public class GuessOutput {
    public static void main(String[] args) {
        int day = 3;
        switch (day) {
            case 1:
                System.out.println("Monday");
            case 2:
                System.out.println("Tuesday");
            case 3:
                System.out.println("Wednesday");
            case 4:
                System.out.println("Thursday");
            default:
                System.out.println("Friday");
        }
    }
}
```
**Answer:** The output will be:
```
Wednesday
Thursday
Friday
```

**Explanation:** The `switch` statement starts executing from `case 3`, printing "Wednesday". Since there are no `break` statements, it continues executing the subsequent cases, printing "Thursday" and "Friday".

#### 35. Guess the output of this switch block?
**Question:** What will be the output of the following code?
```java
public class GuessOutput {
    public static void main(String[] args) {
        int day = 5;
        switch (day) {
            case 1:
                System.out.println("Monday");
                break;
            case 2:
                System.out.println("Tuesday");
                break;
            case 3:
                System.out.println("Wednesday");
                break;
            case 4:
                System.out.println("Thursday");
                break;
            default:
                System.out.println("Friday");
        }
    }
}
```
**Answer:** The output will be:
```
Friday
```

**Explanation:** Since `day` is 5, which doesn't match any case, the `default` case is executed, printing "Friday".

#### 36. Should default be the last case in a switch statement?
**Answer:** Yes, the `default` case is typically the last case in a `switch` statement. This **convention** improves code readability and ensures that the `default` case acts as a catch-all for any unhandled values.

#### 37. Can a switch statement be used around a String?
**Answer:** Yes, starting from Java 7, the `switch` statement can be used with `String` values.

**Example:**
```java
public class StringSwitch {
    public static void main(String[] args) {
        String day = "Wednesday";
        switch (day) {
            case "Monday":
                System.out.println("First day of the week");
                break;
            case "Wednesday":
                System.out.println("Midweek");
                break;
            default:
                System.out.println("Another day");
        }
    }
}
```

#### 38. What is an enhanced for loop?
**Answer:** The enhanced for loop, also known as the "for-each" loop, is used to iterate over arrays and collections in a more readable way.

