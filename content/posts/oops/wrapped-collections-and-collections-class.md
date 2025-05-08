---
title: "Wrapped Collections and Collections Class"
date: 2025-05-08T22:49:57+05:30
draft: false
tags: ["Java", "Collections", "Wrapped Collections", "Collections Class", "OOP"]
categories: ["OOPs"]
---

## Wrapped Collections and Collections Class

In Java, the **Collections** class is a utility class that provides various static methods to operate on or return collections. The **Wrapped Collections** refers to collections that are decorated with additional behavior like thread safety or immutability.

---

### Wrapped Collections

Wrapped collections are used to extend the functionality of existing collections. The `Collections` class in Java provides methods like `synchronizedList()`, `unmodifiableList()`, and others to "wrap" a collection with added functionality.

1. **Synchronized Collections**:
   - `Collections.synchronizedList()`, `Collections.synchronizedSet()`, and `Collections.synchronizedMap()` are methods used to wrap a collection and make it thread-safe. These collections ensure that all access is synchronized.

   ```java
   List<String> names = Collections.synchronizedList(new ArrayList<>());
   names.add("Alice");
   names.add("Bob");
```

2. **Unmodifiable Collections**:

   * `Collections.unmodifiableList()`, `Collections.unmodifiableSet()`, and `Collections.unmodifiableMap()` create collections that cannot be modified once they are created. These are often used to provide read-only access to a collection.

   ```java
   List<String> names = Collections.unmodifiableList(new ArrayList<>(Arrays.asList("Alice", "Bob")));
   ```

3. **Checked Collections**:

   * `Collections.checkedList()`, `Collections.checkedSet()`, and `Collections.checkedMap()` wrap a collection and enforce type safety. They ensure that only objects of the specified type can be added to the collection.

   ```java
   List<String> names = Collections.checkedList(new ArrayList<>(), String.class);
   ```

---

### Collections Class

The **Collections** class provides static methods that operate on collections or return new collections. These methods are commonly used for sorting, shuffling, and performing other operations.

#### Key Methods in Collections Class

1. **sort(List<T> list)**:

   * Sorts the specified list into ascending order based on the natural ordering of its elements.

   ```java
   List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5);
   Collections.sort(numbers);
   ```

2. **shuffle(List\<?> list)**:

   * Randomly permutes the elements of the specified list.

   ```java
   Collections.shuffle(numbers);
   ```

3. **reverse(List\<?> list)**:

   * Reverses the order of the elements in the specified list.

   ```java
   Collections.reverse(numbers);
   ```

4. **max(Collection\<? extends T> coll)**:

   * Returns the maximum element in the collection based on natural ordering or a comparator.

   ```java
   Integer max = Collections.max(numbers);
   ```

5. **min(Collection\<? extends T> coll)**:

   * Returns the minimum element in the collection based on natural ordering or a comparator.

   ```java
   Integer min = Collections.min(numbers);
   ```

6. **fill(List\<? super T> list, T obj)**:

   * Fills the specified list with the specified element.

   ```java
   Collections.fill(numbers, 0);
   ```

7. **frequency(Collection\<?> c, Object o)**:

   * Returns the number of occurrences of the specified element in the collection.

   ```java
   int frequency = Collections.frequency(numbers, 1);
   ```

---

### Example: Using Wrapped Collections and Collections Class

```java
import java.util.*;

public class WrappedCollectionsExample {
    public static void main(String[] args) {
        // Using synchronized collection
        List<String> names = Collections.synchronizedList(new ArrayList<>());
        names.add("Alice");
        names.add("Bob");

        // Using unmodifiable collection
        List<String> unmodifiableNames = Collections.unmodifiableList(new ArrayList<>(Arrays.asList("Alice", "Bob")));
        
        // Using checked collection
        List<String> checkedNames = Collections.checkedList(new ArrayList<>(), String.class);
        checkedNames.add("Charlie");

        // Collections class methods
        List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5);
        
        // Sorting
        Collections.sort(numbers);
        
        // Shuffling
        Collections.shuffle(numbers);
        
        // Finding max
        Integer max = Collections.max(numbers);
        System.out.println("Max: " + max);

        // Finding min
        Integer min = Collections.min(numbers);
        System.out.println("Min: " + min);
    }
}
```

---

### 🔗 Related Notes

* [Collections]({{< ref "posts/oops/collections.md" >}})
* [Map and SortedMap]({{< ref "posts/oops/map-and-sortedmap.md" >}})
* [List]({{< ref "posts/oops/list.md" >}})
