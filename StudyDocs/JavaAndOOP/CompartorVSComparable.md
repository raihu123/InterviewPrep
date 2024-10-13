### Comparable
Comparable Interface has compareTo

- Purpose: Defines the natural ordering of objects.
- Implementation: Implemented by the **class** itself.
- Mnemonic: "I can compare myself."
- Think of it as the object knowing how to compare itself with another object of the same type.
- Basically class comes with the necessary way to compare the objects.
```java
public class Person implements Comparable<Person> {
    @Override
    public int compareTo(Person other) {
        // Comparison logic
    }
}
```

Using comparable but chaining. So assume, compare first name then compare last name 

```java
@Override
public int compareTo(Person other) {
    // The first name is String type so comparing String
    int firstNameComparison = this.firstName.compareTo(other.firstName);
    if (firstNameComparison != 0) {
        return firstNameComparison;
    }
    return this.lastName.compareTo(other.lastName);
}
```

Built in compareTo exsits in Integer and String. 
For example 
- Natural Order `.stream().sorted() // natural order` or 
`.sorted((n1, n2) -> n1.compareTo(n2)) // Not necessary`
- Reversed Order `.sorted((n1, n2) -> n2.compareTo(n1)) // Reverse order` or 
`stream.sorted(Comparator.reverseOrder());`


### Comparator
Basically a interface to used as lambda. So that we can create custom comparsion techniques. This is very imporatant as it is decoupled from classes and everything. May be reused

- Purpose: Defines an external comparison logic, allowing multiple ways to compare objects.
- Implementation: Implemented outside the class, often using anonymous classes or lambda expressions.
- Mnemonic: "I compare others."
- Imagine a separate entity (comparator) that knows how to compare two objects.

Example of comparing and then comparing 

```java
Comparator<Person> byFirstThenLastName = Comparator
    .comparing(Person::getFirstName)
    .thenComparing(Person::getLastName);
```
Alternative appraoch without method references. 
```java
Comparator<Person> byFirstThenLastName = Comparator
    .comparing(x -> x.getFirstName())
    .thenComparing(x -> x.getLastName());
```


Reverse Ordering technique

```java
List<Person> sortedPeople = people.stream()
    .sorted(
        Comparator.comparing(Person::getAge, Comparator.reverseOrder())
                  .thenComparing(Person::getFirstName. Comparator.reverseOrder())
    )
    .collect(Collectors.toList());
```


