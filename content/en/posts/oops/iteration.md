---
title: "Iteration"
date: 2025-05-08T22:45:11+05:30
draft: false
tags: ["Java", "Iteration", "Collections", "OOP"]
categories: ["OOPs"]
---

## Iteration

**Iteration** in Java refers to the process of iterating or traversing through a collection (such as a `List`, `Set`, or `Map`) to access its elements. Iteration is a crucial aspect of working with collections in Java and can be performed using various techniques like `for`, `while`, `do-while` loops, and using the `Iterator` interface.

---

### Iterating Over Collections Using Different Methods

1. **Using For-each Loop**:
   - The simplest and most concise method of iterating over collections.

   ```java
   List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
   for (String name : names) {
       System.out.println(name);
   }
```

2. **Using Iterator**:

   * The `Iterator` interface provides methods like `hasNext()` and `next()` to iterate through the elements in a collection.

   ```java
   Iterator<String> iterator = names.iterator();
   while (iterator.hasNext()) {
       System.out.println(iterator.next());
   }
   ```

3. **Using forEach Method (Java 8+)**:

   * Java 8 introduced the `forEach()` method that allows iterating over collections in a functional style.

   ```java
   names.forEach(name -> System.out.println(name));
   ```

4. **Using ListIterator (For Lists)**:

   * `ListIterator` is specifically used for iterating over `List` objects and provides additional methods like `add()`, `set()`, and bi-directional iteration.

   ```java
   ListIterator<String> listIterator = names.listIterator();
   while (listIterator.hasNext()) {
       System.out.println(listIterator.next());
   }
   ```

---

### Benefits of Iteration

* **Simplifies Data Access**: Iteration provides an easy and consistent way to access and process elements in a collection.

* **Flexibility**: Different iteration techniques cater to specific needs such as traversing a collection in reverse order, modifying elements during iteration, or performing actions on each element.

* **Functional Programming**: With Java 8+, iteration can be performed using lambda expressions and streams, enabling a more declarative style of coding.

---

### Example: Iterating Through a Set

```java
import java.util.*;

public class IterationExample {
    public static void main(String[] args) {
        Set<String> names = new HashSet<>(Arrays.asList("Alice", "Bob", "Charlie"));

        // Using Iterator
        Iterator<String> iterator = names.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}
```

---

### 🔗 Related Notes

* [Collections]({{< ref "en/posts/oops/collections.md" >}})
* [Iterator Interface]({{< ref "en/posts/oops/iteration-and-collection-interface.md" >}})

