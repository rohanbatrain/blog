---
title: "Program Control Statements"
date: 2025-05-08T19:02:17+05:30
draft: false
tags: ["Java", "Control Statements"]
categories: ["OOPs"]
---

## 🔄 Program Control Statements in Java

Control statements in Java allow you to dictate the flow of execution in your program. They can be broadly categorized into conditional, looping, and branching statements.

---

### 🧠 Types of Control Statements

1. **Conditional Statements**
   - `if`, `else`, `else if`: Used to make decisions in code.

   ```java
   int a = 10, b = 20;
   if (a > b) {
       System.out.println("a is greater");
   } else {
       System.out.println("b is greater");
   }
```

2. **Switch Statement**

   * Used for multiple condition checks, simplifying `if-else if` chains.

   ```java
   int day = 3;
   switch (day) {
       case 1: System.out.println("Monday"); break;
       case 2: System.out.println("Tuesday"); break;
       default: System.out.println("Invalid day");
   }
   ```

3. **Looping Statements**

   * **for**: Repeats code a set number of times.
   * **while**: Executes code while a condition is true.
   * **do-while**: Executes code at least once, then checks the condition.

   ```java
   // For Loop Example
   for (int i = 0; i < 5; i++) {
       System.out.println(i);
   }
   ```

4. **Branching Statements**

   * **break**: Exits a loop or switch statement.
   * **continue**: Skips the current iteration of a loop.

   ```java
   // Continue Example
   for (int i = 0; i < 5; i++) {
       if (i == 3) continue;  // Skip the iteration when i is 3
       System.out.println(i);
   }
   ```

---

### 🧪 Example: Conditional and Looping Control

```java
public class ControlStatementsExample {
    public static void main(String[] args) {
        int num = 5;
        
        if (num > 0) {
            System.out.println("Positive number");
        }

        // For Loop
        for (int i = 1; i <= 3; i++) {
            System.out.println("Iteration " + i);
        }
    }
}
```

---


### 🔗 Related Notes
* [Variables]({{< ref "en/posts/oops/variables.md" >}})
* [Operators]({{< ref "en/posts/oops/operators.md" >}})
* [Arrays]({{< ref "en/posts/oops/arrays.md" >}})
* [Strings]({{< ref "en/posts/oops/strings.md" >}})
