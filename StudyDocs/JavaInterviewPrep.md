## OOP Concepts
Remember using : *A PIE*

### Abstraction:

Abstraction hides *complex* implementation an exposing the necessary features.
- Abstract Classes (Will have at least 1 abstract method may have many multiple 
- Interfaces (No concrete methods may have static and/or default methods) 

### Polymorphism:

Polymorphism allows objects to be treated as instances of their parent class rather than their actual class.

**Types of Polymorphism:**
1.  **Compile-time Polymorphism (Static Binding or Method Overloading):**
2.  **Runtime Polymorphism (Dynamic Binding or Method Overriding):**

### Inheritance: 

Inheritance provides an object with the ability to acquire the fields and methods of another class, called base class. Inheritance provides re-usability of code and can be used to add additional features to an existing class, without modifying it.

### Encapsulation:

Encapsulation provides objects with the ability to hide their internal characteristics and behavior. Each object provides a number of methods, which can be accessed by other objects and change its internal data. In Java, there are three access modifiers: public, private and protected. Each modifier imposes different access rights to other classes, either in the same or in external packages. Some of the advantages of using encapsulation are listed below: 
- The internal state of every objected is protected by hiding its attributes. 
- It increases usability and maintenance of code, because the behavior of an object can be independently changed or extended. 
- It improves modularity by preventing objects to interact with each other, in an undesired way. 

#### What is JVM ? Why is Java called the Platform Independent Programming Language?

 A Java virtual machine (JVM) executes Java bytecode. 
 Java files converted to bytecode (JVM executes bytecode)
 JVM are developed as per the Platform need but the bytecode will run on any JVM or Platform. 

 
 #### What is the Difference between JDK and JRE ? 
 
 The Java Runtime Environment (JRE) is basically the Java Virtual Machine (JVM) where your Java programs are being executed. It also includes browser plugins for applet execution. The Java Development Kit (JDK) is the full featured Software Development Kit for Java, including the JRE, the compilers and tools (like JavaDoc, and Java Debugger), in order for a user to develop, compile and execute Java applications. 
 
 #### What does the “static” keyword mean ? Can you override private or static method in Java ? 
 
 Static keyword enables us to access a variable or method without instantiating a class 
 - No override of static methods *(because static is defined at compile time and overriding happens at runtime)
 
 #### Can you access non static variable in static context ? 
 
A static variable in Java belongs to its class and its value remains the same for all its instances. A static variable is initialized when the class is loaded by the JVM. If your code tries to access a non-static variable, without any instance, the compiler will complain, because those variables are not created yet and they are not associated with any instance. 

#### Wrapper Classes in Java

Wrapper classes in Java are classes that provide a way to use primitive data types (int, char, etc.) as objects
#### Wrapper Class Creation : 
-   **Using Constructors:**
    -   Every call to the constructor creates a new object.
    -   Example: `new Integer(10)` always creates a new `Integer` object.
-   **Using Factory Methods:**
    -   The `valueOf` method may return a cached object, improving performance and reducing memory usage.
    -   Example: `Integer.valueOf(10)` may return a cached instance for frequently used values (like small integers).

#### What is Auto-boxing and Unboxing ?

Autoboxing is the automatic conversion made by the Java compiler between the primitive types and their corresponding object wrapper classes. For example, the compiler converts an int to an Integer, a double to a Double, and so on. If the conversion goes the other way, this operation is called unboxing.

#### What is Casting?

Casting is the process of converting a variable from one type to another. In Java, casting can be either implicit (automatic) or explicit (manual).

#### Implicit-casting/Widening/Up casting

Implicit casting is the automatic conversion of a smaller data type to a larger data type. This is safe and does not result in data loss.
```java
int intVal = 100;
long longVal = intVal; // Implicit casting from int to long
```

#### Explicit casting /Narrow /Down casting

Explicit casting is the manual conversion of a larger data type to a smaller data type. This can result in data loss and requires explicit syntax.
```java
long longVal = 100L;
int intVal = (int) longVal; // Explicit casting from long to int
```

**Are all Strings immutable?** 
All `String` objects are immutable. This means once a `String` object is created, its value cannot be changed. Any modification to a `String` results in the creation of a new `String` object.

### String Memory Storage

**Where are String values stored in memory?** 
String values are stored in a special memory area called the String Pool (or interned strings pool) within the heap memory. When a `String` literal is created, Java checks the pool first to see if the same value already exists. If it does, the reference to the existing string is returned. If it doesn't, a new `String` object is created and added to the pool.

### String Concatenation in Loops

**Why should you be careful about the String concatenation (`+`) operator in loops?**
Using the `+` operator for String concatenation in loops is inefficient because each concatenation creates a new `String` object, resulting in multiple temporary objects and significant memory overhead.

### Solving the String Concatenation Problem

**How do you solve the above problem?** 
To solve this problem, use `StringBuilder` or `StringBuffer` for concatenating strings within loops. These classes are mutable and designed for efficient string manipulation without creating multiple temporary objects.

### Differences Between String and StringBuffer

**String:**

-   Immutable: Once created, its value cannot be changed.
-   Thread-safe: Since it's immutable, it's inherently thread-safe.
-   Performance: Slower for concatenation operations.

**StringBuffer:**

-   Mutable: Its value can be changed.
-   Thread-safe: Synchronized methods make it thread-safe.
-   Performance: Slower than `StringBuilder` due to synchronization but faster than `String` for concatenation operations.

### Differences Between StringBuilder and StringBuffer

**StringBuilder:**

-   Mutable: Its value can be changed.
-   Not thread-safe: Not synchronized, so not safe for use by multiple threads.
-   Performance: Faster than `StringBuffer` because it doesn't have the overhead of synchronization.

**StringBuffer:**

-   Mutable: Its value can be changed.
-   Thread-safe: Synchronized methods make it thread-safe.
-   Performance: Slower than `StringBuilder` due to synchronization.

### Utility Methods in the String Class

**Examples of Different Utility Methods in the String Class:**

1.  **`length()`**
    
    -   Returns the length of the string.
    
    `String str = "Hello";
    int length = str.length(); // 5` 
    
2.  **`charAt(int index)`**
    
    -   Returns the character at the specified index.
    
    `char ch = str.charAt(1); // 'e'` 
    
3.  **`substring(int beginIndex, int endIndex)`**
    
    -   Returns a new string that is a substring of this string.
    
    `String sub = str.substring(1, 4); // "ell"` 
    
4.  **`indexOf(String str)`**
    -   Returns the index of the first occurrence of the specified substring.    
    `int index = str.indexOf("l"); // 2` 
    
5.  **`equals(Object anObject)`**
    
    -   Compares this string to the specified object.
    `boolean isEqual = str.equals("Hello"); // true` 
    
6.  **`toLowerCase()`**
    -   Converts all of the characters in this string to lowercase.
    `String lower = str.toLowerCase(); // "hello"` 
    
7.  **`toUpperCase()`**
    -   Converts all of the characters in this string to uppercase.
    `String upper = str.toUpperCase(); // "HELLO"` 
    
8.  **`trim()`**
    -   Returns a copy of the string with leading and trailing whitespace removed
    `String trimmed = "  Hello  ".trim(); // "Hello"` 
    
9.  **`replace(char oldChar, char newChar)`**
    -   Returns a new string resulting from replacing all occurrences of `oldChar` in this string with `newChar`.
    `String replaced = str.replace('l', 'p'); // "Heppo"` 
    
10.  **`split(String regex)`**
    -   Splits this string around matches of the given regular expression.
    ```String[] parts = str.split("l"); // ["He", "", "o"]```


### Object-Oriented Programming Concepts

#### 23. What is a class?
A class is a blueprint or template for creating objects. It defines a type of object according to the methods and properties (variables) that the objects created from the class will have.

**Example:**
```java
public class Car {
    String color;
    String model;
    int year;
    
    void drive() {
        System.out.println("The car is driving.");
    }
}
```

#### 24. What is an object?
An object is an instance of a class. It is a real-world entity that has a state and behavior defined by its class.

**Example:**
```java
Car myCar = new Car();
myCar.color = "Red";
myCar.model = "Tesla Model 3";
myCar.year = 2020;
myCar.drive(); // Outputs: The car is driving.
```

#### 25. What is the state of an object?
The state of an object refers to the values of its instance variables (properties) at any given time.

**Example:**
In the example above, the state of `myCar` includes its `color` (Red), `model` (Tesla Model 3), and `year` (2020).

#### 26. What is the behavior of an object?
The behavior of an object is defined by the methods of its class, which describe the actions that the object can perform.

**Example:**
In the `Car` class, the `drive()` method represents the behavior of a car object.

#### 27. What is the superclass of every class in Java?
The superclass of every class in Java is `java.lang.Object`. It is the root of the class hierarchy and every class in Java implicitly extends `Object`.

#### 28. Explain the `toString` method.
The `toString` method returns a string representation of the object. By default, it returns the class name followed by the `@` sign and the object's hashcode, but it can be overridden to provide a more meaningful representation.

**Example:**
```java
public class Car {
    String color;
    String model;
    int year;
    
    @Override
    public String toString() {
        return "Car [color=" + color + ", model=" + model + ", year=" + year + "]";
    }
    
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.color = "Red";
        myCar.model = "Tesla Model 3";
        myCar.year = 2020;
        System.out.println(myCar.toString()); // Outputs: Car [color=Red, model=Tesla Model 3, year=2020]
    }
}
```

#### 29. What is the use of the `equals` method in Java?
The `equals` method is used to compare two objects for equality. The default implementation in the `Object` class compares memory addresses, but it can be overridden to compare object contents.

#### 30. What are the important things to consider when implementing the `equals` method?
1. **Symmetry:** `a.equals(b)` should return the same result as `b.equals(a)`.
2. **Reflexivity:** `a.equals(a)` should always return true.
3. **Transitivity:** If `a.equals(b)` and `b.equals(c)`, then `a.equals(c)` should return true.
4. **Consistency:** Multiple invocations of `a.equals(b)` should consistently return true or false.
5. **Null comparison:** `a.equals(null)` should return false.

#### 31. What is the `hashCode` method used for in Java?
The `hashCode` method returns an integer hash code that is used for the efficient location of objects in hash-based collections like `HashMap`, `HashSet`, etc. It is important to override `hashCode` whenever `equals` is overridden.

### Inheritance

#### 32. Explain inheritance with examples.
Inheritance is a mechanism where a new class (subclass) inherits properties and behaviors (methods) from an existing class (superclass).

**Example:**
```java
class Animal {
    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("The dog barks.");
    }
    
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.eat(); // Inherited method
        myDog.bark(); // Method of Dog class
    }
}
```

#### 33. What is method overloading?
Method overloading occurs when a class has multiple methods with the same name but different parameters (type, number, or both) also can have different return types as wellf.

**Example:**
```java
class MathUtils {
    int add(int a, int b) {
        return a + b;
    }
    
    double add(double a, double b) {
        return a + b;
    }
}
```

#### 34. What is method overriding?
Method overriding occurs when a subclass provides a specific implementation for a method that is already defined in its superclass.

**Example:**
```java
class Animal {
    void makeSound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Dog barks");
    }
}
```

#### 35. Can a superclass reference variable hold an object of a subclass?
Yes, a superclass reference variable can hold an object of a subclass. This is known as upcasting.

**Example:**

```java
Animal myDog = new Dog();
myDog.makeSound(); // Outputs: Dog barks
```
**If the Child Class has an extra method, And we are using its Parents Reference Type, then that method will not be accessable until the Reference Type is the Child Type.**

```java

class HelloWorld {
    public static void main(String[] args) {
        A b = new B();
        b.methodA(); // methodAClassB
        // b.methodB();// THis will give compiler error
        B b2 = (B) b;
        b2.methodA(); // methodAClassB
        b2.methodB(); // method.B
    }
    
    static class A{
        void methodA(){
            System.out.println("method A");
        }
    }
    static class B extends A{
        void methodA(){
            System.out.println("methodAClassB");
        }
        void methodB(){
            System.out.println("method.B");
        }
    }
}
```

#### What is covariant return types ? 

Covariant return types in Java allow an overridden method in a subclass to return a more specific type than the method in the superclass. This enhances type safety by allowing more precise return types without breaking the method's contract.

**Limitations:**
- Inheritance Hierarchy: The return type of the overriding method must be a subclass of the return type declared in the parent interface or abstract class.
- Type Consistency: The method signature must remain consistent in other aspects (parameters, name, etc.), only the return type is allowed to vary covariantly.
- No Contravariant Parameters: While return types can be covariant, method parameters cannot be contravariant (i.e., you cannot change parameter types in the overriding method).

### Example:
```java
class Animal {
    Animal getAnimal() {
        return new Animal();
    }
}

class Dog extends Animal {
    @Override
    Dog getAnimal() {
        return new Dog();
    }
}

interface AnimalProvider {
    Animal getAnimal();
}

class DogProvider implements AnimalProvider {
    @Override
    Dog getAnimal() {
        return new Dog();
    }
}

abstract class AnimalProvider {
    abstract Animal getAnimal();
}

class DogProvider extends AnimalProvider {
    @Override
    Dog getAnimal() {
        return new Dog();
    }
}

```

In this example, `Dog` overrides `getAnimal` and specifies `Dog` as the return type, which is a subtype of `Animal`.

#### 36. Is multiple inheritance allowed in Java?
Multiple inheritance is not allowed in Java for classes. However, a class can implement multiple interfaces.

### Interfaces

#### 37. What is an interface?
An interface in Java is a reference type, similar to a class, that can contain only constants, method signatures, default methods, static methods, and nested types. Interfaces cannot have instance fields or constructors.

#### 38. How do you define an interface?
An interface is defined using the `interface` keyword.

**Example:**
```java
interface Animal {
    void makeSound();
}
```

#### 39. How do you implement an interface?
A class implements an interface using the `implements` keyword.

**Example:**
```java
class Dog implements Animal {
    public void makeSound() {
        System.out.println("Dog barks");
    }
}
```

#### What happens when a class implements multiple interface in java but they have the same name but different paramaeter or return type? 

When a class in Java implements multiple interfaces that have methods with the same name but different parameters (method overloading), the class must implement each version of the method. 
*If the methods have the same name and parameters but different return types, this will cause a compile-time error because Java does not allow method overloading based solely on return type.*


#### 40. Can you explain a few tricky things about interfaces?
- **Multiple Inheritance:** A class can implement multiple interfaces, providing a way to achieve multiple inheritance.
- **Default Methods:** Introduced in Java 8, interfaces can have default methods with implementation.
- **Static Methods:** Interfaces can have static methods.
- **Functional Interfaces:** Interfaces with a single abstract method are functional interfaces and can be used with lambda expressions.

#### 41. Can you extend an interface?
Yes, an interface can extend another interface, inheriting its abstract methods.

**Example:**
```java
interface Animal {
    void eat();
}

interface Dog extends Animal {
    void bark();
}
```

#### 42. Can a class implement multiple interfaces?
Yes, a class can implement multiple interfaces.

**Example:**

```java
class Dog implements Animal, Pet {
    public void eat() {
        System.out.println("Dog eats");
    }
    
    public void play() {
        System.out.println("Dog plays");
    }
}
```

### Abstract Classes

#### 43. What is an abstract class?
An abstract class is a class that cannot be instantiated and is meant to be subclassed. It can contain abstract methods (methods without implementation) and concrete methods (methods with implementation).

#### 44. When do you use an abstract class?
Use an abstract class when you want to define a common base class with some default behavior but allow subclasses to provide specific implementations for some methods.

#### 45. How do you define an abstract method?
An abstract method is defined using the `abstract` keyword and does not have a body.

**Example:**
```java
abstract class Animal {
    abstract void makeSound();
}
```

#### 46. Compare abstract class vs interface.
- **Abstract Class:** Can have both abstract and concrete methods, instance variables, and constructors. Supports single inheritance.
- **Interface:** Can only have abstract methods (until Java 8), constants, default, and static methods. Supports multiple inheritance.

### Constructors

#### 47. What is a constructor?
A constructor is a special method that is called when an object is instantiated. It is used to initialize the object's state.

#### 48. What is a default constructor?
A default constructor is a no-argument constructor provided by Java if no other constructors are defined in the class.

**Example:**
```java
class Car {
    // Default constructor
    Car() {
        System.out.println("Car is created");
    }
}
```

#### 49. Will this code compile?
```java
class Car {
    Car(int year) {
        System.out.println("Car is created in year " + year);
    }
    
    public static void main(String[] args) {
        Car myCar = new Car();
    }
}
```
**Answer:** No, this code will not compile because the `Car` class does not have a no-argument constructor, and an attempt to instantiate it with `new Car()` will result in a compile-time error.

#### 50. How do you call a superclass constructor from a constructor?
You can call a superclass constructor using the `super` keyword.

**Example:**
```java
class Vehicle {
    Vehicle(String name) {
        System.out.println("Vehicle name is " + name);
    }
}

class Car extends Vehicle {
    Car(String name) {
        super(name); // Call to superclass constructor
        System.out.println("Car is created");
    }
}
```

#### 51. Will this code compile?
```java
class Car {
    Car() {
        System.out.println("Car is created");
    }
}

class ElectricCar extends Car {
    ElectricCar() {
        System.out.println("ElectricCar is created");
    }
    
    public static void main(String[] args) {
        ElectricCar myCar = new ElectricCar();
    }
}
```
**Answer:** Yes, this code will compile and produce the following output:
```
Car is created
ElectricCar is created
```
The compiler will introduce a `super()` this will be only done if the Parent has a default or no argument constructor.

#### 52. What is the use of `this()`?
The `this()` keyword is used to call another constructor in the same class. It is useful for constructor chaining.

**Example:**
```java
class Car {
    Car() {
        this("Unknown");
        System.out.println("Default constructor called");
    }
    
    Car(String name) {
        System.out.println("Car name is " + name);
    }
}
```

#### 53. Can a constructor be called directly from a method?
No, a constructor cannot be called directly from a method. Constructors can only be called during the creation of an object using the `new` keyword or through constructor chaining using `this()` or `super()`.

#### 54. Is a superclass constructor called even when there is no explicit call from a subclass constructor?
Yes, if there is no explicit call to the superclass constructor, the default no-argument constructor of the superclass is automatically called. If the superclass does not have a no-argument constructor, a compile-time error will occur.

**Example:**
```java
class Vehicle {
    Vehicle() {
        System.out.println("Vehicle is created");
    }
}

class Car extends Vehicle {
    Car() {
        System.out.println("Car is created");
    }
    
    public static void main(String[] args) {
        Car myCar = new Car();
    }
}
```
**Output:**
```
Vehicle is created
Car is created
```
