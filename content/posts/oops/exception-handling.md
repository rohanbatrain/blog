---
title: "Exception Handling"
date: 2025-05-08T21:09:26+05:30
draft: false
tags: ["OOP", "Java", "Exceptions"]
categories: ["OOPs"]
---

## Exception Handling

**Exception Handling** in Java is a powerful mechanism that handles runtime errors to maintain the normal flow of application execution. Java provides a robust and object-oriented way to handle exceptions using `try`, `catch`, `throw`, `throws`, and `finally` blocks.

### Why Use Exception Handling?
- Avoid abnormal termination of the program.
- Gracefully handle unexpected situations like file not found, divide by zero, etc.
- Help in debugging and maintaining the code.

---

### Keywords in Exception Handling

1. **try** – Defines a block of code to test for errors.
2. **catch** – Defines a block of code to handle errors.
3. **finally** – Defines a block of code that will always execute after try/catch, regardless of the outcome.
4. **throw** – Used to explicitly throw an exception.
5. **throws** – Declares exceptions that a method might throw.

---

### Example:
```java
public class ExceptionExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;  // ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Error: " + e.getMessage());
        } finally {
            System.out.println("This will always execute.");
        }
    }
}
````

**Output:**

```
Error: / by zero
This will always execute.
```

---

### Types of Exceptions

1. **Checked Exceptions** – Must be handled at compile time (e.g., IOException).
2. **Unchecked Exceptions** – Occur during runtime and are not required to be caught (e.g., ArithmeticException, NullPointerException).
3. **Errors** – Serious problems not intended to be caught (e.g., OutOfMemoryError).

---

### 🔗 Related Notes

* [Exception Handlers]({{< ref "posts/oops/exception-handlers.md" >}})
* [Nested Classes]({{< ref "posts/oops/nested-classes.md" >}})
* [Types of Nested Classes]({{< ref "posts/oops/types-of-nested-classes.md" >}})
* [Thread Class]({{< ref "posts/oops/thread-class.md" >}})

