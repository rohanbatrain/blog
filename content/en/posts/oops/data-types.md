---
title: "Data Types"
date: 2025-05-08T18:58:37+05:30
draft: false
tags: ["Java", "Data Types"]
categories: ["OOPs"]
---

## 🔢 Data Types in Java

Java is a **strongly typed language**, meaning each variable must be declared with a specific data type. Java supports two main categories of data types: **primitive** and **reference** types.

---

### 🏷️ Primitive Data Types

Java has eight primitive data types, each with a specific size and value range:

1. **byte** – 1 byte, range: -128 to 127
2. **short** – 2 bytes, range: -32,768 to 32,767
3. **int** – 4 bytes, range: -2^31 to 2^31-1
4. **long** – 8 bytes, range: -2^63 to 2^63-1
5. **float** – 4 bytes, single-precision floating point
6. **double** – 8 bytes, double-precision floating point
7. **char** – 2 bytes, represents a single character
8. **boolean** – 1 bit, either `true` or `false`

---

### 🧱 Reference Data Types

Reference types are objects, arrays, or any other instance of a class. They do not hold the actual data but refer to the memory location where the data is stored.

- **String** – Sequence of characters (reference type, not primitive).
- **Arrays** – Reference type that holds a fixed number of elements of a specified type.

---

### 🧪 Example

```java
public class DataTypesExample {
    public static void main(String[] args) {
        int x = 5;              // primitive data type
        String message = "Hi";  // reference data type

        System.out.println("Integer: " + x);
        System.out.println("String: " + message);
    }
}
```

---



### 🔗 Related Notes
* [Variables]({{< ref "en/posts/oops/variables.md" >}})
* [Operators]({{< ref "en/posts/oops/operators.md" >}})
* [Program Control Statements]({{< ref "en/posts/oops/program-control-statements.md" >}})
* [Arrays]({{< ref "en/posts/oops/arrays.md" >}})
* [Strings]({{< ref "en/posts/oops/strings.md" >}})
