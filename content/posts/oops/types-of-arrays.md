---
title: "Types of Arrays"
date: 2025-05-08T19:05:58+05:30
draft: false
tags: ["Java", "Arrays", "Types"]
categories: ["OOPs"]
---

## 📊 Types of Arrays in Java

Arrays in Java can be classified into two types: **Single-Dimensional Arrays** and **Multidimensional Arrays**. Both types store elements of the same data type, but their structure differs.

---

### 🧑‍🏫 1. Single-Dimensional Arrays

A single-dimensional array is a linear list of elements, where each element is accessed via its index.

#### 🔹 Example

```java
int[] numbers = {10, 20, 30, 40, 50};
System.out.println("Element at index 2: " + numbers[2]);  // Output: 30
```

#### 🔹 Declaring and Initializing

```java
int[] arr = new int[5];  // Declaring with fixed size
arr[0] = 1;               // Assigning values
```

---

### 📐 2. Multidimensional Arrays

Multidimensional arrays are arrays of arrays. A **2D array** is the most common, where each element is itself an array.

#### 🔹 Example: 2D Array

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};
System.out.println("Element at [1][1]: " + matrix[1][1]);  // Output: 5
```

#### 🔹 Declaring a 2D Array

```java
int[][] matrix = new int[2][3];  // 2 rows, 3 columns
matrix[0][0] = 1;                 // Assigning values
matrix[0][1] = 2;
```

---

### 🔺 3. Jagged Arrays (Array of Arrays)

A jagged array is an array of arrays where each array can have different lengths.

#### 🔹 Example: Jagged Array

```java
int[][] jaggedArray = new int[3][];
jaggedArray[0] = new int[2];  // First row has 2 elements
jaggedArray[1] = new int[3];  // Second row has 3 elements
jaggedArray[2] = new int[1];  // Third row has 1 element
```

---

### 🧪 Example: Accessing Elements of Different Types of Arrays

```java
public class ArrayTypesExample {
    public static void main(String[] args) {
        // Single-Dimensional Array
        int[] numbers = {10, 20, 30};
        System.out.println("Single-Dimensional Array: " + numbers[1]);

        // Multidimensional Array
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6}
        };
        System.out.println("Multidimensional Array: " + matrix[1][2]);

        // Jagged Array
        int[][] jagged = new int[2][];
        jagged[0] = new int[3];
        jagged[1] = new int[2];
        System.out.println("Jagged Array: " + jagged[0].length); // Output: 3
    }
}
```

---


### 🔗 Related Notes
* [Arrays]({{< ref "posts/oops/arrays.md" >}})
* [Data Types]({{< ref "posts/oops/data-types.md" >}})
