---
title: "Input Output Statements"
date: 2025-05-08T18:56:18+05:30
draft: false
tags: ["Java", "IO", "Basics"]
categories: ["OOPs"]
---

## 🖨️ Input/Output Statements in Java

Java provides various mechanisms to **accept input** from the user and **display output** to the screen, typically using classes from the `java.io` and `java.util` packages.

---

### 📥 Input in Java

The most common way to accept user input is through the `Scanner` class.

#### 🔹 Example Using `Scanner`

```java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter your name: ");
        String name = sc.nextLine();
        System.out.println("Hello, " + name);
    }
}
```

---

### 📤 Output in Java

Java uses `System.out.println()` and `System.out.print()` for output.

* `System.out.println()` – prints with a newline
* `System.out.print()` – prints without a newline

#### 🔹 Example

```java
System.out.println("Hello, world!"); // newline
System.out.print("Hello, ");         // no newline
System.out.print("Java!");           // continues on same line
```

---

### 🔍 Other I/O Options

* `BufferedReader` (legacy, more control)
* `Console` (secure password entry)
* `FileReader`, `FileWriter` (for file I/O)

---

### 🔗 Related Notes

* [Features of Java]({{< ref "posts/oops/features-of-java.md" >}})
* [Command Line Arguments]({{< ref "posts/oops/command-line-arguments.md" >}})
