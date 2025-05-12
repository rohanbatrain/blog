---
title: "Iteration and Collection Interface"
date: 2025-05-08T22:51:25+05:30
draft: false
tags: ["Java", "Iteration", "Collection Interface", "OOP"]
categories: ["OOPs"]
---

## Iteration and Collection Interface

In Java, iteration refers to the process of accessing elements of a collection in a sequence. The **Collection Interface** is a root interface for all collections in the Java Collections Framework. It provides the basic functionality that all collections share, such as adding, removing, and checking elements.

---

### Collection Interface

The `Collection` interface is part of the Java Collections Framework and defines the common methods used to work with collections of objects. Some of the key methods defined in the `Collection` interface include:

1. **add(E e)**:
   - Adds the specified element to the collection.

   ```java
   Collection<String> collection = new ArrayList<>();
   collection.add("Alice"); 
   ```

2. **remove(Object o)**:

   * Removes a single instance of the specified element from the collection.

   ```java
   collection.remove("Alice");
   ```

3. **contains(Object o)**:

   * Returns `true` if the collection contains the specified element.

   ```java
   boolean containsAlice = collection.contains("Alice");
   ```

4. **size()**:

   * Returns the number of elements in the collection.

   ```java
   int size = collection.size();
   ```

5. **clear()**:

   * Removes all elements from the collection.

   ```java
   collection.clear();
   ```

6. **isEmpty()**:

   * Returns `true` if the collection contains no elements.

   ```java
   boolean isEmpty = collection.isEmpty();
   ```

7. **toArray()**:

   * Returns an array containing all the elements of the collection.

   ```java
   Object[] array = collection.toArray();
   ```

---

### Iteration in Java

To iterate over the elements in a collection, Java provides several mechanisms, such as the **Iterator**, **Enhanced for-loop**, and **Streams**.

#### 1. **Iterator Interface**

The `Iterator` interface is part of the Java Collections Framework and provides methods to traverse a collection. The methods in `Iterator` are:

* **hasNext()**: Returns `true` if the iteration has more elements.
* **next()**: Returns the next element in the iteration.
* **remove()**: Removes the current element from the collection.

```java
Iterator<String> iterator = collection.iterator();
while (iterator.hasNext()) {
    String element = iterator.next();
    System.out.println(element);
}
```

#### 2. **Enhanced for-loop**

The enhanced for-loop (also known as the "for-each" loop) is a simple and concise way to iterate over elements in a collection.

```java
for (String name : collection) {
    System.out.println(name);
}
```

#### 3. **Streams API (Java 8 and above)**

Java 8 introduced the **Streams API**, which provides a functional approach to iterate over collections. Using streams, you can filter, map, and reduce collections in a very concise manner.

```java
collection.stream()
          .filter(name -> name.startsWith("A"))
          .forEach(System.out::println);
```

---

### Example: Iterating Over a Collection

```java
import java.util.*;

public class CollectionIterationExample {
    public static void main(String[] args) {
        Collection<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");

        // Using Iterator
        Iterator<String> iterator = names.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }

        // Using Enhanced for-loop
        for (String name : names) {
            System.out.println(name);
        }

        // Using Streams
        names.stream()
             .filter(name -> name.startsWith("A"))
             .forEach(System.out::println);
    }
}
```

---

### 🔗 Related Notes

* [Collection Interface]({{< ref "en/posts/oops/collection-interface.md" >}})