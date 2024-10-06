Here's a comprehensive cheatsheet that covers various modifications you can perform on an `ArrayList` using Java's Stream API. This list includes examples of common operations like filtering, transforming, sorting, and more.

### **1. Initialize an ArrayList Using Streams**
```java
List<Integer> numbers = IntStream.range(1, 11).boxed().collect(Collectors.toList());
// Creates a list with values: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### **2. Filtering an ArrayList**
- **Filter Even Numbers**:
```java
List<Integer> evenNumbers = numbers.stream()
                                   .filter(n -> n % 2 == 0)
                                   .collect(Collectors.toList());
// Output: [2, 4, 6, 8, 10]
```

- **Filter Strings by Length**:
```java
List<String> words = Arrays.asList("Java", "Stream", "API", "Example");
List<String> longWords = words.stream()
                              .filter(word -> word.length() > 3)
                              .collect(Collectors.toList());
// Output: [Java, Stream, Example]
```

### **3. Transforming Elements (Mapping)**
- **Convert a List of Integers to Their Squares**:
```java
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .collect(Collectors.toList());
// Output: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

- **Convert All Strings to Uppercase**:
```java
List<String> upperCaseWords = words.stream()
                                   .map(String::toUpperCase)
                                   .collect(Collectors.toList());
// Output: [JAVA, STREAM, API, EXAMPLE]
```

### **4. Sorting an ArrayList**
- **Sort Numbers in Ascending Order**:
```java
List<Integer> sortedNumbers = numbers.stream()
                                     .sorted()
                                     .collect(Collectors.toList());
// Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

- **Sort Strings Alphabetically**:
```java
List<String> sortedWords = words.stream()
                                .sorted()
                                .collect(Collectors.toList());
// Output: [API, Example, Java, Stream]
```

- **Sort Strings by Length**:
```java
List<String> sortedByLength = words.stream()
                                   .sorted(Comparator.comparingInt(String::length))
                                   .collect(Collectors.toList());
// Output: [API, Java, Stream, Example]
```

### **5. Reducing a List to a Single Value**
- **Find the Sum of All Elements**:
```java
int sum = numbers.stream()
                 .reduce(0, Integer::sum);
// Output: 55
```

- **Concatenate All Strings in the List**:
```java
String concatenated = words.stream()
                           .reduce("", (acc, word) -> acc + word);
// Output: "JavaStreamAPIExample"
```

### **6. Collecting into a Different Collection Type**
- **Convert List to Set**:
```java
Set<Integer> numberSet = numbers.stream()
                                .collect(Collectors.toSet());
// Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

- **Convert List to a Map (Word to Length)**:
```java
Map<String, Integer> wordLengthMap = words.stream()
                                          .collect(Collectors.toMap(word -> word, word -> word.length()));
// Output: {Java=4, Stream=6, API=3, Example=7}
```

### **7. Removing Duplicates**
```java
List<Integer> withDuplicates = Arrays.asList(1, 2, 3, 3, 4, 5, 5, 6);
List<Integer> withoutDuplicates = withDuplicates.stream()
                                                .distinct()
                                                .collect(Collectors.toList());
// Output: [1, 2, 3, 4, 5, 6]
```

### **8. Skipping and Limiting Results**
- **Skip First 3 Elements**:
```java
List<Integer> skipped = numbers.stream()
                               .skip(3)
                               .collect(Collectors.toList());
// Output: [4, 5, 6, 7, 8, 9, 10]
```

- **Limit to First 5 Elements**:
```java
List<Integer> limited = numbers.stream()
                               .limit(5)
                               .collect(Collectors.toList());
// Output: [1, 2, 3, 4, 5]
```

### **9. Grouping Elements**
- **Group Words by Their Length**:
```java
Map<Integer, List<String>> groupedByLength = words.stream()
                                                  .collect(Collectors.groupingBy(String::length));
// Output: {3=[API], 4=[Java], 6=[Stream], 7=[Example]}
```

### **10. Joining Elements as a String**
- **Join All Words into a Single String**:
```java
String joined = words.stream()
                     .collect(Collectors.joining(", "));
// Output: "Java, Stream, API, Example"
```

### **11. Parallel Stream for Faster Processing**
```java
List<Integer> squaresParallel = numbers.parallelStream()
                                       .map(n -> n * n)
                                       .collect(Collectors.toList());
// Output: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100] (Order may vary)
```

### **12. Peek for Debugging During Stream Operations**
`peek` is useful for debugging intermediate stream operations.
```java
List<Integer> result = numbers.stream()
                              .peek(n -> System.out.println("Processing: " + n))
                              .map(n -> n * n)
                              .peek(n -> System.out.println("Square: " + n))
                              .collect(Collectors.toList());
// Output:
// Processing: 1
// Square: 1
// Processing: 2
// Square: 4
// ...
```

### **13. Flattening Nested Collections**
If you have a list of lists, you can **flatten** it into a single list.

```java
List<List<Integer>> listOfLists = Arrays.asList(
    Arrays.asList(1, 2, 3),
    Arrays.asList(4, 5, 6),
    Arrays.asList(7, 8, 9)
);

List<Integer> flatList = listOfLists.stream()
                                    .flatMap(List::stream)
                                    .collect(Collectors.toList());
// Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### **14. Counting Elements**
- **Count Elements Greater Than 5**:
```java
long count = numbers.stream()
                    .filter(n -> n > 5)
                    .count();
// Output: 5
```

### **15. Finding Minimum and Maximum Values**
- **Find Maximum Value**:
```java
int max = numbers.stream()
                 .max(Integer::compareTo)
                 .orElseThrow(NoSuchElementException::new);
// Output: 10
```

- **Find Minimum Value**:
```java
int min = numbers.stream()
                 .min(Integer::compareTo)
                 .orElseThrow(NoSuchElementException::new);
// Output: 1
```

### **16. All Match, Any Match, None Match**
- **Check if All Elements Are Positive**:
```java
boolean allPositive = numbers.stream()
                             .allMatch(n -> n > 0);
// Output: true
```

- **Check if Any Element is Greater Than 8**:
```java
boolean anyGreaterThanEight = numbers.stream()
                                     .anyMatch(n -> n > 8);
// Output: true
```

- **Check if No Element is Negative**:
```java
boolean noneNegative = numbers.stream()
                              .noneMatch(n -> n < 0);
// Output: true
```

### **17. Using `forEach` for Simple Iteration**
```java
numbers.stream()
       .forEach(n -> System.out.println("Number: " + n));
// Output: Number: 1, Number: 2, ..., Number: 10
```

### **18. Using `Map` to Modify Object Properties**
For a list of custom objects, you can modify a field using `map`.

```java
class Person {
    String name;
    int age;
    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    @Override
    public String toString() {
        return name + " - " + age;
    }
}

List<Person> people = Arrays.asList(
    new Person("Alice", 25),
    new Person("Bob", 30),
    new Person("Charlie", 35)
);

List<Person> updatedAges = people.stream()
                                 .map(person -> new Person(person.name, person.age + 1))
                                 .collect(Collectors.toList());
// Output: [Alice - 26, Bob - 31, Charlie - 36]
```
