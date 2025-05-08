---
title: "Concurrent Programming"
date: 2025-05-08T21:11:21+05:30
draft: false
tags: ["OOP", "Java", "Multithreading"]
categories: ["OOPs"]
---

## Concurrent Programming

**Concurrent Programming** in Java allows multiple threads to run simultaneously, making programs more efficient and responsive, especially for tasks that are independent or I/O-bound.

### Why Concurrency?
- Efficient CPU utilization
- Better performance in multi-core systems
- Responsiveness in interactive applications

---

### Threads in Java

Java supports multithreading through the `Thread` class and `Runnable` interface. A thread represents a single sequence of execution within a program.

---

### Creating Threads

#### 1. By Extending `Thread` Class
```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running...");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start();  // Starts a new thread
    }
}
```

#### 2. By Implementing `Runnable` Interface

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable thread running...");
    }
}

public class Main {
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable());
        t.start();
    }
}
```

---

### Thread Lifecycle

1. New
2. Runnable
3. Running
4. Blocked/Waiting
5. Terminated

---

### Synchronization

Used to control thread access to shared resources to prevent data inconsistency.

```java
synchronized void printTable(int n) {
    for (int i = 1; i <= 5; i++) {
        System.out.println(n * i);
    }
}
```

---

### 🔗 Related Notes

* [Thread Class]({{< ref "posts/oops/thread-class.md" >}})
* [Runnable Interface]({{< ref "posts/oops/runnable-interface.md" >}})
* [Exception Handling]({{< ref "posts/oops/exception-handling.md" >}})
