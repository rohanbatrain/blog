---
title: "Set and Sortedset"
date: 2025-05-08T22:46:41+05:30
draft: false
tags: ["Java", "Set", "SortedSet", "Collections", "OOP"]
categories: ["OOPs"]
---

## Set and SortedSet

In Java, the **Set** and **SortedSet** interfaces represent collections of unique elements. While the `Set` interface simply enforces uniqueness, the `SortedSet` interface builds upon `Set` by maintaining its elements in a sorted order. Both interfaces are part of the Java Collections Framework and are primarily used when uniqueness and ordering are required.

---

### Set Interface

The **Set** interface extends the `Collection` interface and does not allow duplicate elements. The most commonly used implementations of `Set` are:

1. **HashSet**:
   - A `HashSet` is backed by a hash table and does not maintain the order of its elements.

   ```java
   Set<String> names = new HashSet<>();
   names.add("Alice");
   names.add("Bob");
```

2. **LinkedHashSet**:

   * A `LinkedHashSet` is similar to `HashSet` but maintains the insertion order of elements.

   ```java
   Set<String> names = new LinkedHashSet<>();
   names.add("Alice");
   names.add("Bob");
   ```

3. **TreeSet**:

   * A `TreeSet` implements the `SortedSet` interface and maintains elements in ascending order (based on their natural ordering or a comparator).

   ```java
   Set<Integer> numbers = new TreeSet<>();
   numbers.add(3);
   numbers.add(1);
   numbers.add(2);
   ```

---

### SortedSet Interface

The **SortedSet** interface extends the `Set` interface and ensures that elements are stored in a sorted order. It provides additional methods that are not available in `Set`:

1. **first()**:

   * Returns the first (lowest) element in the set.

   ```java
   SortedSet<Integer> numbers = new TreeSet<>();
   numbers.add(3);
   numbers.add(1);
   numbers.add(2);
   System.out.println(numbers.first()); // Output: 1
   ```

2. **last()**:

   * Returns the last (highest) element in the set.

   ```java
   System.out.println(numbers.last()); // Output: 3
   ```

3. **subSet()**:

   * Returns a view of the portion of the set whose elements range from `fromElement` to `toElement`.

   ```java
   SortedSet<Integer> subSet = numbers.subSet(1, 3);
   ```

---

### Example: Using Set and SortedSet

```java
import java.util.*;

public class SetAndSortedSetExample {
    public static void main(String[] args) {
        // Using HashSet
        Set<String> names = new HashSet<>();
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");

        System.out.println("Names in HashSet: " + names);
        
        // Using TreeSet (SortedSet)
        SortedSet<Integer> numbers = new TreeSet<>();
        numbers.add(5);
        numbers.add(1);
        numbers.add(3);
        
        System.out.println("Numbers in TreeSet: " + numbers);
        System.out.println("First element: " + numbers.first());
        System.out.println("Last element: " + numbers.last());
    }
}
```

---

### 🔗 Related Notes

* [Collections]({{< ref "en/posts/oops/collections.md" >}})
* [List Interface]({{< ref "en/posts/oops/list.md" >}})
* [Iterator Interface]({{< ref "en/posts/oops/iteration-and-collection-interface.md" >}})
