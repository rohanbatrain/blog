---
title: "Runnable Interface"
date: 2025-05-08T21:15:37+05:30
draft: false
tags: ["OOP", "Java", "Multithreading"]
categories: ["OOPs"]
---

## Runnable Interface

The `Runnable` interface in Java is another way to create and execute threads. It is preferred over extending the `Thread` class, especially when a class needs to extend another class as Java does not support multiple inheritance.

---

### Declaring a Thread with Runnable

To use `Runnable`, implement the interface and pass the object to a `Thread`.

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable thread running...");
    }
}

public class Main {
    public static void main(String[] args) {
        MyRunnable myRunnable = new MyRunnable();
        Thread t = new Thread(myRunnable);
        t.start();
    }
}
```

---

### Advantages of Using Runnable

* **Decouples task from thread mechanics.**
* **Allows class to extend another class.**
* **More flexible in multithreaded applications.**

---

### Anonymous Runnable Example

```java
public class Main {
    public static void main(String[] args) {
        Thread t = new Thread(new Runnable() {
            public void run() {
                System.out.println("Anonymous Runnable running...");
            }
        });
        t.start();
    }
}
```

---

### Functional Interface & Lambda Expression (Java 8+)

```java
public class Main {
    public static void main(String[] args) {
        Runnable r = () -> System.out.println("Lambda Runnable running...");
        Thread t = new Thread(r);
        t.start();
    }
}
```

---

### 🔗 Related Notes

* [Thread Class]({{< ref "posts/oops/thread-class.md" >}})
* [Concurrent Programming]({{< ref "posts/oops/concurrent-programming.md" >}})
* [Exception Handlers]({{< ref "posts/oops/exception-handlers.md" >}})

