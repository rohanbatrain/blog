---
title: "Command Line Arguments"
date: 2025-05-08T18:57:32+05:30
draft: false
tags: ["Java", "Command Line", "Basics"]
categories: ["OOPs"]
---

## 🧾 Command Line Arguments in Java

**Command Line Arguments** allow users to pass input parameters to the program **when it is executed**, enabling dynamic behavior without changing code.

---

### 🧠 Concept

Java's `main()` method accepts an array of `String` arguments:

```java
public static void main(String[] args)
```

* `args` holds the command line values as strings.
* `args[0]`, `args[1]`, etc. refer to individual arguments.

---

### 🧪 Example

```java
public class CmdArgs {
    public static void main(String[] args) {
        System.out.println("Number of arguments: " + args.length);
        for (int i = 0; i < args.length; i++) {
            System.out.println("Arg " + i + ": " + args[i]);
        }
    }
}
```

#### 🔹 Running the program:

```bash
java CmdArgs Alice Bob
```

#### 🔹 Output:

```
Number of arguments: 2
Arg 0: Alice
Arg 1: Bob
```

---

### ⚠️ Notes

* All inputs are read as `String`. You must parse them (e.g., `Integer.parseInt()`) if needed.
* Handle cases when arguments are missing to avoid `ArrayIndexOutOfBoundsException`.

---

### 🔗 Related Notes

* [Input Output Statements]({{< ref "en/posts/oops/input-output-statements.md" >}})
* [Features of Java]({{< ref "en/posts/oops/features-of-java.md" >}})

