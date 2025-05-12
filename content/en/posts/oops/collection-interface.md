---
title: "Collection Interface"
date: 2025-05-08T22:45:41+05:30
draft: false
tags: ["Java", "Collection Interface", "OOP", "Collections"]
categories: ["OOPs"]
---

## Collection Interface

The **Collection Interface** is the root interface of the Java Collections Framework. It represents a group of objects, known as elements. The `Collection` interface provides fundamental methods to work with elements, such as adding, removing, and querying elements in a collection. All other collection interfaces (`Set`, `List`, `Queue`, etc.) extend this interface.

---

### Key Methods in Collection Interface

1. **add(E e)**:
   - Adds the specified element to the collection. Returns `true` if the element was successfully added.

   ```java
   collection.add("Alice");
    ```

2. **remove(Object o)**:

   * Removes the specified element from the collection. Returns `true` if the element was found and removed.

   ```java
   collection.remove("Alice");
   ```

3. **size()**:

   * Returns the number of elements in the collection.

   ```java
   int size = collection.size();
   ```

4. **isEmpty()**:

   * Checks if the collection is empty. Returns `true` if the collection contains no elements.

   ```java
   boolean empty = collection.isEmpty();
   ```

5. **contains(Object o)**:

   * Checks if the collection contains the specified element.

   ```java
   boolean hasAlice = collection.contains("Alice");
   ```

6. **clear()**:

   * Removes all elements from the collection.

   ```java
   collection.clear();
   ```

7. **iterator()**:

   * Returns an iterator that can be used to traverse the elements of the collection.

   ```java
   Iterator<E> iterator = collection.iterator();
   ```

---

### Example: Using Collection Interface

```java
import java.util.*;

public class CollectionInterfaceExample {
    public static void main(String[] args) {
        // Creating a Collection (List implementation)
        Collection<String> names = new ArrayList<>();
        
        // Adding elements
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");
        
        // Iterating through the collection
        for (String name : names) {
            System.out.println(name);
        }
        
        // Removing an element
        names.remove("Bob");
        
        // Checking if an element is present
        boolean hasAlice = names.contains("Alice");
        System.out.println("Contains Alice: " + hasAlice);
        
        // Size of collection
        System.out.println("Size: " + names.size());
        
        // Clearing the collection
        names.clear();
    }
}
```

---

### 🔗 Related Notes

* [Collections]({{< ref "en/posts/oops/collections.md" >}})
* [Set and SortedSet]({{< ref "en/posts/oops/set-and-sortedset.md" >}})
* [List Interface]({{< ref "en/posts/oops/list.md" >}})
* [Iterator Interface]({{< ref "en/posts/oops/iteration-and-collection-interface.md" >}})

