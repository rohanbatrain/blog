---
title: "Collections"
date: 2025-05-08T22:39:52+05:30
categories: ["OOPs"]
draft: false
tags: ["Java", "Collections", "OOP", "List", "Set", "Map"]
---

## Collections

In Java, the **Collections Framework** is a unified architecture for representing and manipulating collections of objects. It provides a set of interfaces, implementations, and algorithms to handle various types of data collections like lists, sets, and maps. The `java.util` package contains all the collection classes and interfaces.

---

### Core Interfaces of Collections Framework

1. **Collection Interface**:
   - The root interface of the collection hierarchy. It defines common operations like `add()`, `remove()`, `size()`, and `clear()`, which are implemented by all other collection classes.

2. **Set Interface**:
   - Represents a collection of unique elements (no duplicates). Common implementations include `HashSet`, `TreeSet`, and `LinkedHashSet`.

3. **List Interface**:
   - Represents an ordered collection that allows duplicate elements. Common implementations include `ArrayList`, `LinkedList`, and `Vector`.

4. **Map Interface**:
   - Represents a collection of key-value pairs, where each key is unique. Common implementations include `HashMap`, `TreeMap`, and `LinkedHashMap`.

5. **SortedSet and SortedMap**:
   - Specialized versions of `Set` and `Map` that maintain their elements in a sorted order. `TreeSet` implements `SortedSet` and `TreeMap` implements `SortedMap`.

---

### Benefits of Using Collections Framework

1. **Efficiency**:
   - Provides efficient and optimized algorithms for storing and manipulating collections.
   
2. **Reusability**:
   - The framework allows you to reuse implementations for common data structures such as lists, sets, and maps.

3. **Flexibility**:
   - The framework provides a variety of collections, each tailored to specific use cases (e.g., `HashSet` for fast lookups, `ArrayList` for dynamic arrays).

4. **Interoperability**:
   - The various implementations of the core interfaces are interchangeable, allowing you to switch between them with minimal changes to your code.

---

### Example: Using Collections to Store Data

```java
import java.util.*;

public class CollectionsExample {
    public static void main(String[] args) {
        // Using a List to store elements
        List<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");

        // Using an Iterator to iterate over the collection
        Iterator<String> iterator = names.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}
```

---

### 🔗 Related Notes

* [Iterator and Collection Interface]({{< ref "en/posts/oops/iteration-and-collection-interface.md" >}})
* [Set Interface]({{< ref "en/posts/oops/set-and-sortedset.md" >}})
* [List Interface]({{< ref "en/posts/oops/list.md" >}})
* [Map Interface]({{< ref "en/posts/oops/map-and-sortedmap.md" >}})

