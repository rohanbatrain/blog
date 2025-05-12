---
title: "Arrays"
date: 2025-05-08T19:04:43+05:30
draft: false
tags: ["Java", "Arrays"]
categories: ["OOPs"]
---

## 🧑‍💻 Arrays in Java

An **array** is a data structure in Java that stores multiple values of the same type in a single variable. It provides a way to group variables under a single name, making it easier to manage and manipulate data.

---

### 🌱 Declaring and Initializing Arrays

1. **Declaring an Array**
   - Syntax: `dataType[] arrayName;`

   ```java
   int[] arr;  // Declaration
```

2. **Initializing an Array**

   * **Static Initialization**: Assigning values at the time of declaration.

   ```java
   int[] arr = {1, 2, 3, 4, 5};  // Initialization
   ```

   * **Dynamic Initialization**: Assigning values later.

   ```java
   int[] arr = new int[5];  // Creates an array of size 5
   arr[0] = 1;  // Assign values
   arr[1] = 2;
   ```

---

### 🚀 Example: Using Arrays

```java
public class ArraysExample {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};
        
        // Accessing array elements
        System.out.println("First Element: " + numbers[0]);
        
        // Iterating over array
        for (int i = 0; i < numbers.length; i++) {
            System.out.println("Element at index " + i + ": " + numbers[i]);
        }
    }
}
```

---

### 🔍 Multidimensional Arrays

Java also supports arrays with multiple dimensions, like 2D arrays.

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};
```

---

### 🧪 Example: Multidimensional Array

```java
public class MultidimensionalArrayExample {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2},
            {3, 4}
        };

        System.out.println("Element at [1][1]: " + matrix[1][1]);  // Output: 4
    }
}
```

---


### 🔗 Related Notes
* [Variables]({{< ref "en/posts/oops/variables.md" >}})
* [Operators]({{< ref "en/posts/oops/operators.md" >}})
* [Program Control Statements]({{< ref "en/posts/oops/program-control-statements.md" >}})
* [Strings]({{< ref "en/posts/oops/strings.md" >}})
