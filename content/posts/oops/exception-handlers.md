---
title: "Exception Handlers"
date: 2025-05-08T21:10:41+05:30
draft: false
tags: ["OOP", "Java", "Exceptions"]
categories: ["OOPs"]
---

## Exception Handlers

**Exception Handlers** in Java are constructs used to handle exceptions that occur during the execution of a program. The primary way to handle exceptions is by using `try`, `catch`, and `finally` blocks.

### try-catch Block

The `try` block contains code that might throw an exception. The `catch` block handles the exception type declared in its parameter.

```java
try {
    int[] arr = new int[5];
    arr[10] = 50; // This will throw ArrayIndexOutOfBoundsException
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Caught exception: " + e);
}
```

---

### Multiple catch Blocks

You can catch different types of exceptions separately.

```java
try {
    String str = null;
    System.out.println(str.length());
} catch (NullPointerException e) {
    System.out.println("NullPointerException caught");
} catch (Exception e) {
    System.out.println("General Exception caught");
}
```

---

### finally Block

The `finally` block is executed whether an exception is handled or not.

```java
try {
    int result = 25 / 5;
} catch (ArithmeticException e) {
    System.out.println("Caught ArithmeticException");
} finally {
    System.out.println("Finally block executed");
}
```

---

### Nested try-catch

You can nest `try-catch` blocks inside other `try` blocks.

```java
try {
    try {
        int data = 50 / 0;
    } catch (ArithmeticException e) {
        System.out.println("Inner catch: " + e);
    }
} catch (Exception e) {
    System.out.println("Outer catch: " + e);
}
```

---

### Best Practices

* Catch specific exceptions before general ones.
* Avoid catching `Throwable` unless absolutely necessary.
* Use `finally` for cleanup operations like closing resources.

---

### 🔗 Related Notes

* [Exception Handling]({{< ref "posts/oops/exception-handling.md" >}})
* [Thread Class]({{< ref "posts/oops/thread-class.md" >}})
* [Runnable Interface]({{< ref "posts/oops/runnable-interface.md" >}})

