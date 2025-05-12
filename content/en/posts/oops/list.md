---
title: "List"
date: 2025-05-08T22:47:56+05:30
draft: false
tags: ["Java", "List", "Collections", "OOP"]
categories: ["OOPs"]
---

## List

The **List** interface is a part of the Java Collections Framework and represents an ordered collection that can contain duplicate elements. Unlike `Set`, a `List` maintains the order in which elements are inserted and allows for random access to its elements via an index.

---

### Key Implementations of List

1. **ArrayList**:
   - An `ArrayList` is a resizable array implementation of the `List` interface. It provides fast random access to elements but can be slower when adding or removing elements at arbitrary positions (except at the end).

   ```java
   List<String> names = new ArrayList<>();
   names.add("Alice");
   names.add("Bob");
```

2. **LinkedList**:

   * A `LinkedList` is a doubly linked list implementation of the `List` interface. It offers better performance than `ArrayList` when adding or removing elements from the beginning or middle of the list.

   ```java
   List<String> names = new LinkedList<>();
   names.add("Alice");
   names.add("Bob");
   ```

3. **Vector**:

   * A `Vector` is similar to an `ArrayList`, but it is synchronized, making it thread-safe. However, its usage has been largely replaced by `ArrayList`.

   ```java
   List<String> names = new Vector<>();
   names.add("Alice");
   names.add("Bob");
   ```

---

### Important Methods in List

1. **add(E e)**:

   * Adds the specified element to the list.

   ```java
   list.add("Alice");
   ```

2. **get(int index)**:

   * Retrieves the element at the specified position in the list.

   ```java
   String name = list.get(0); // Access first element
   ```

3. **remove(int index)**:

   * Removes the element at the specified position.

   ```java
   list.remove(0); // Removes the first element
   ```

4. **set(int index, E element)**:

   * Replaces the element at the specified position with the specified element.

   ```java
   list.set(0, "New Name");
   ```

5. **contains(Object o)**:

   * Checks if the list contains the specified element.

   ```java
   boolean containsAlice = list.contains("Alice");
   ```

6. **size()**:

   * Returns the number of elements in the list.

   ```java
   int size = list.size();
   ```

---

### Example: Using List

```java
import java.util.*;

public class ListExample {
    public static void main(String[] args) {
        // Creating a List
        List<String> names = new ArrayList<>();
        
        // Adding elements
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");
        
        // Retrieving an element
        System.out.println("First element: " + names.get(0)); // Output: Alice
        
        // Removing an element
        names.remove("Bob");
        
        // Checking size
        System.out.println("Size of list: " + names.size());
        
        // Iterating through the list
        for (String name : names) {
            System.out.println(name);
        }
    }
}
```

---

### 🔗 Related Notes

* [Collections]({{< ref "en/posts/oops/collections.md" >}})
* [Set and SortedSet]({{< ref "en/posts/oops/set-and-sortedset.md" >}})
* [Iterator Interface]({{< ref "en/posts/oops/iteration-and-collection-interface.md" >}})

