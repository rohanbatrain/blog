---
title: "Map and Sortedmap"
date: 2025-05-08T22:48:57+05:30
draft: false
tags: ["Java", "Map", "SortedMap", "Collections", "OOP"]
categories: ["OOPs"]
---

## Map and SortedMap

In Java, the **Map** and **SortedMap** interfaces are part of the Java Collections Framework. The `Map` interface represents a collection of key-value pairs, where each key is unique, and each key maps to exactly one value. The `SortedMap` interface extends `Map` and guarantees that the keys are sorted in a specific order.

---

### Map Interface

The **Map** interface defines a collection of key-value pairs. The key is used to retrieve its corresponding value. Common implementations of `Map` include `HashMap`, `LinkedHashMap`, and `TreeMap`.

#### Common Methods in Map Interface

1. **put(K key, V value)**:
   - Inserts the specified key-value pair into the map.

   ```java
   map.put("name", "Alice");
````

2. **get(Object key)**:

   * Retrieves the value associated with the specified key.

   ```java
   String value = map.get("name");
   ```

3. **remove(Object key)**:

   * Removes the key-value pair for the specified key.

   ```java
   map.remove("name");
   ```

4. **containsKey(Object key)**:

   * Checks if the map contains the specified key.

   ```java
   boolean hasName = map.containsKey("name");
   ```

5. **containsValue(Object value)**:

   * Checks if the map contains the specified value.

   ```java
   boolean hasValue = map.containsValue("Alice");
   ```

6. **size()**:

   * Returns the number of key-value pairs in the map.

   ```java
   int size = map.size();
   ```

7. **keySet()**:

   * Returns a set view of the keys contained in the map.

   ```java
   Set<K> keys = map.keySet();
   ```

8. **values()**:

   * Returns a collection view of the values contained in the map.

   ```java
   Collection<V> values = map.values();
   ```

---

### SortedMap Interface

The **SortedMap** interface extends `Map` and guarantees that its keys are sorted. It provides additional methods to navigate through the map based on key order.

#### Additional Methods in SortedMap

1. **firstKey()**:

   * Returns the first (lowest) key in the sorted map.

   ```java
   K firstKey = sortedMap.firstKey();
   ```

2. **lastKey()**:

   * Returns the last (highest) key in the sorted map.

   ```java
   K lastKey = sortedMap.lastKey();
   ```

3. **headMap(K toKey)**:

   * Returns a view of the portion of the map whose keys are less than `toKey`.

   ```java
   SortedMap<K, V> headMap = sortedMap.headMap("C");
   ```

4. **tailMap(K fromKey)**:

   * Returns a view of the portion of the map whose keys are greater than or equal to `fromKey`.

   ```java
   SortedMap<K, V> tailMap = sortedMap.tailMap("B");
   ```

5. **subMap(K fromKey, K toKey)**:

   * Returns a view of the portion of the map whose keys range from `fromKey` to `toKey`.

   ```java
   SortedMap<K, V> subMap = sortedMap.subMap("A", "D");
   ```

---

### Example: Using Map and SortedMap

```java
import java.util.*;

public class MapAndSortedMapExample {
    public static void main(String[] args) {
        // Using HashMap (Map implementation)
        Map<String, Integer> map = new HashMap<>();
        map.put("Alice", 30);
        map.put("Bob", 25);
        
        System.out.println("Value for Alice: " + map.get("Alice"));
        System.out.println("Contains Bob: " + map.containsKey("Bob"));
        
        // Using TreeMap (SortedMap implementation)
        SortedMap<String, Integer> sortedMap = new TreeMap<>();
        sortedMap.put("Alice", 30);
        sortedMap.put("Bob", 25);
        sortedMap.put("Charlie", 35);
        
        System.out.println("First key: " + sortedMap.firstKey());
        System.out.println("Last key: " + sortedMap.lastKey());
        
        // Iterating through the sorted map
        for (Map.Entry<String, Integer> entry : sortedMap.entrySet()) {
            System.out.println(entry.getKey() + " = " + entry.getValue());
        }
    }
}
```

---

### 🔗 Related Notes

* [Collections]({{< ref "posts/oops/collections.md" >}})
* [Set and SortedSet]({{< ref "posts/oops/set-and-sortedset.md" >}})
* [List]({{< ref "posts/oops/list.md" >}})
