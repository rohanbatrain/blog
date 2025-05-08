---
title: "Strings"
date: 2025-05-08T19:08:17+05:30
draft: false
tags: ["Java", "Strings"]
categories: ["Unit I", "OOPs"]
---

## 📝 Strings in Java

In Java, a **String** is a sequence of characters. It is a widely used class for manipulating text. Strings are immutable, meaning once a string is created, its value cannot be changed.

---

### 🧠 String Characteristics

1. **Immutable**  
   - Once a string object is created, its value cannot be modified. Any operation on a string creates a new string object.

2. **String Pool**  
   - Java maintains a pool of strings to optimize memory usage. If the same string is created multiple times, the JVM reuses the string from the pool instead of creating a new one.

3. **String Length**  
   - The length of a string can be obtained using the `.length()` method.

---

### 🔹 Creating Strings in Java

1. **Using String Literals**
   - When you use a string literal, Java automatically adds it to the string pool.

   ```java
   String str = "Hello, Java!";
````

2. **Using the `new` Keyword**

   * You can create a string explicitly using the `new` keyword, which will create a new object in memory.

   ```java
   String str2 = new String("Hello, Java!");
   ```

---

### 🧪 Example: String Methods

```java
public class StringsExample {
    public static void main(String[] args) {
        String str1 = "Hello";
        String str2 = "World";
        
        // Concatenation
        String result = str1 + " " + str2;
        System.out.println("Concatenation: " + result);

        // Length
        System.out.println("Length of str1: " + str1.length());

        // Convert to Uppercase
        System.out.println("Uppercase: " + str1.toUpperCase());

        // Check if the string contains a substring
        System.out.println("Contains 'Java': " + result.contains("Java"));
    }
}
```

---

### 🔧 Common String Methods

1. **.length()** - Returns the length of the string.
2. **.toUpperCase()** - Converts the string to uppercase.
3. **.toLowerCase()** - Converts the string to lowercase.
4. **.substring()** - Extracts a portion of the string.
5. **.equals()** - Compares two strings for equality.
6. **.charAt()** - Returns the character at a specified index.

---


### 🔗 Related Notes
* [Arrays]({{< ref "posts/oops/arrays.md" >}})
* [Program Control Statements]({{< ref "posts/oops/program-control-statements.md" >}})
* [Variables]({{< ref "posts/oops/variables.md" >}})
* [Operators]({{< ref "posts/oops/operators.md" >}})
* [Types of Arrays]({{< ref "posts/oops/types-of-arrays.md" >}})
