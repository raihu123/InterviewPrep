## OOP Concepts

Remember using: *A PIE*

### Abstraction

Abstraction hides *complex* implementation and exposes the necessary features.
- **Abstract Classes:** Have at least one abstract method and may have multiple concrete methods.
- **Interfaces:** No concrete methods; may have static and/or default methods.

### Polymorphism

Polymorphism allows objects to be treated as instances of their parent class rather than their actual class.

**Types of Polymorphism:**
1. **Compile-time Polymorphism *(Static Binding or Method Overloading)*:** Method overloading allows multiple methods in the same class with the same name but different parameters. In Compile-time Polymorphism (Method Overloading), the return type can be the same or different. The key requirement for method overloading is that the method signatures (i.e., method names and parameter lists) must be different. The return type alone is not sufficient to distinguish overloaded methods.
```java
class MathOperation {
    int add(int a, int b) {
        return a + b;
    }
    double add(double a, double b) {
        return a + b;
    }
    String add(String a, String b) {
        return a + b;
    }
}

```
2. **Runtime Polymorphism *(Dynamic Binding or Method Overriding)*:** Method overriding allows a subclass to provide a specific implementation of a method already defined in its superclass. Also we can have **covariant return type** : an overridden method in a subclass to return a type that is a subclass of the type returned by the method in the superclass.
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
```

### Inheritance

Inheritance provides an object with the ability to acquire the fields and methods of another class, called the base class. It provides reusability of code and allows for additional features to be added to an existing class without modifying it.

### Encapsulation

Encapsulation provides objects with the ability to hide their internal characteristics and behavior. Each object provides a number of methods, which can be accessed by other objects to change its internal data. In Java, there are three access modifiers: public, private, and protected. Each modifier imposes different access rights to other classes, either in the same or in external packages. 

**Advantages of Encapsulation:**
- The internal state of every object is protected by hiding its attributes.
- Increases usability and maintenance of code because the behavior of an object can be independently changed or extended.
- Improves modularity by preventing objects from interacting with each other in an undesired way.

### Questions

1. **What is polymorphism?**  
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

2. **What is the use of `instanceof` operator in Java?**  
   The `instanceof` operator is used to test whether an object is an instance of a specific class or a subclass thereof. It returns `true` if the object is an instance of the specified class or interface, and `false` otherwise.

   **Example:**
   ```java
   Animal myDog = new Dog();
   System.out.println(myDog instanceof Dog); // Outputs: true
   System.out.println(myDog instanceof Animal); // Outputs: true
   System.out.println(myDog instanceof Cat); // Outputs: false
   ```

3. **What is coupling?**  
   Coupling refers to the degree of direct knowledge that one class has of another. There are two types of coupling:
   - **Tight Coupling:** When classes are highly dependent on each other.
   - **Loose Coupling:** When classes are independent or have minimal dependencies.

   Loose coupling is generally preferred as it makes the code more modular, easier to test, and maintain.

4. **What is cohesion?**  
   Cohesion refers to how closely related and focused the responsibilities of a single class or module are. A class with high cohesion performs a single task or a group of related tasks and has clear responsibilities. High cohesion within classes is desirable as it makes the system easier to maintain and understand.

5. **What is encapsulation?**  
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

6. **What is an inner class?**  
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

7. **What is a static inner class?**  
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

8. **Can you create an inner class inside a method?**  
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

9. **What is an anonymous class?**  
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

   ### Association, Composition, and Aggregation in Java

#### Association

**Definition:** Association represents a relationship between two separate classes that establishes through their objects. It defines how objects from one class can be related to objects of another class. Association can be one-to-one, one-to-many, many-to-one, or many-to-many.

**Key Point:** There is no ownership; both classes have their own lifecycle and are independent.

**Example:**
```java
class Teacher {
    String name;
    // constructor, getters, and setters
}

class Course {
    String title;
    // constructor, getters, and setters
}

public class AssociationExample {
    public static void main(String[] args) {
        Teacher teacher = new Teacher("Mr. Smith");
        Course course = new Course("Mathematics");
        // Association between teacher and course
    }
}
```

**Easy to Remember:** Think of a teacher and a course - a teacher can teach many courses, and a course can have many teachers. Neither owns the other.

#### Composition (Part of Relationship)

**Definition:** Composition is a strong form of association with the concept of ownership. If a class is composed of other classes and if the container (owner) object is destroyed, all its contained objects are also destroyed.

**Key Point:** The lifecycle of the contained object depends on the lifecycle of the container object.

**Example:**
```java
class Engine {
    // Engine properties and methods
}

class Car {
    private Engine engine;
    
    Car() {
        engine = new Engine();
    }
    
    // Other properties and methods
}

public class CompositionExample {
    public static void main(String[] args) {
        Car car = new Car();
        // Engine is part of Car, and is destroyed when Car is destroyed
    }
}
```

**Easy to Remember:** Think of a car and its engine. If the car is destroyed, the engine is also destroyed. The engine cannot exist without the car.

#### Aggregation (Has a Relationship)

**Definition:** Aggregation is a weak form of association with the concept of ownership. It represents a relationship where the child can exist independently of the parent.

**Key Point:** The lifecycle of the contained object does not depend on the lifecycle of the container object.

**Example:**
```java
class Department {
    String name;
    // constructor, getters, and setters
}

class Company {
    private List<Department> departments;
    
    Company() {
        departments = new ArrayList<>();
    }
    
    void addDepartment(Department department) {
        departments.add(department);
    }
    
    // Other properties and methods
}

public class AggregationExample {
    public static void main(String[] args) {
        Department dept = new Department("HR");
        Company company = new Company();
        company.addDepartment(dept);
        // Department can exist without the company
    }
}
```

**Easy to Remember:** Think of a company and its departments. A department can exist even if the company does not (e.g., it can move to another company).

### Summary

- **Association:** No ownership. Objects are related but independent.
- **Composition:** Strong ownership. Contained objects cannot exist without the container.
- **Aggregation:** Weak ownership. Contained objects can exist independently of the container.