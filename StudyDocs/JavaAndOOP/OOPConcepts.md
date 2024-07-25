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

### Polymorphism

#### 55. What is polymorphism?
Polymorphism is a core concept in object-oriented programming that allows objects of different types to be treated as objects of a common super type. It provides the ability to call the same method on different objects and have each of them respond in a way appropriate to their type. There are two types of polymorphism in Java: compile-time (method overloading) and runtime (method overriding).

**Example:**
```java
class Animal {
    void makeSound() {
        System.out.println("Some sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Bark");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Meow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        Animal myCat = new Cat();
        
        myDog.makeSound(); // Outputs: Bark
        myCat.makeSound(); // Outputs: Meow
    }
}
```

### The `instanceof` Operator

#### 56. What is the use of `instanceof` operator in Java?
The `instanceof` operator is used to test whether an object is an instance of a specific class or a subclass thereof. It returns `true` if the object is an instance of the specified class or interface, and `false` otherwise.

**Example:**
```java
Animal myDog = new Dog();
System.out.println(myDog instanceof Dog); // Outputs: true
System.out.println(myDog instanceof Animal); // Outputs: true
System.out.println(myDog instanceof Cat); // Outputs: false
```

### Coupling

#### 57. What is coupling?
Coupling refers to the degree of direct knowledge that one class has of another. There are two types of coupling:
- **Tight Coupling:** When classes are highly dependent on each other.
- **Loose Coupling:** When classes are independent or have minimal dependencies.

Loose coupling is generally preferred as it makes the code more modular, easier to test, and maintain.

### Cohesion

#### 58. What is cohesion?
Cohesion refers to how closely related and focused the responsibilities of a single class or module are. A class with high cohesion performs a single task or a group of related tasks and has clear responsibilities. High cohesion within classes is desirable as it makes the system easier to maintain and understand.

### Encapsulation

#### 59. What is encapsulation?
Encapsulation is an object-oriented principle that restricts direct access to an object's data and methods. Instead, access is provided through public methods (getters and setters). It helps in protecting the internal state of the object and promotes modularity and maintainability.

**Example:**
```java
public class Person {
    private String name;
    private int age;
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public int getAge() {
        return age;
    }
    
    public void setAge(int age) {
        this.age = age;
    }
}
```

### Inner Classes

#### 60. What is an inner class?
An inner class is a class defined within another class. It has access to the members of the outer class, including private members. Inner classes are used to logically group classes that are only used in one place and to increase encapsulation.

**Example:**
```java
public class OuterClass {
    private String outerField = "Outer";

    class InnerClass {
        void display() {
            System.out.println("Outer field: " + outerField);
        }
    }
}
```

#### 61. What is a static inner class?
A static inner class is a nested class that is declared static. It can be instantiated without an instance of the outer class and does not have access to non-static members of the outer class.

**Example:**
```java
public class OuterClass {
    static class StaticInnerClass {
        void display() {
            System.out.println("Inside static inner class");
        }
    }
    
    public static void main(String[] args) {
        StaticInnerClass inner = new StaticInnerClass();
        inner.display(); // Outputs: Inside static inner class
    }
}
```

#### 62. Can you create an inner class inside a method?
Yes, you can create an inner class inside a method. Such classes are called local inner classes.

**Example:**
```java
public class OuterClass {
    void myMethod() {
        class LocalInnerClass {
            void display() {
                System.out.println("Inside local inner class");
            }
        }
        
        LocalInnerClass inner = new LocalInnerClass();
        inner.display(); // Outputs: Inside local inner class
    }
}
```

### Anonymous Classes

#### 63. What is an anonymous class?
An anonymous class is a class without a name that is declared and instantiated in a single expression. It is often used to make an instance of an object with certain "extras" or to override methods of a class or interface.

**Example:**
```java
public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal() {
            void makeSound() {
                System.out.println("Anonymous animal sound");
            }
        };
        
        myAnimal.makeSound(); // Outputs: Anonymous animal sound
    }
}
```
