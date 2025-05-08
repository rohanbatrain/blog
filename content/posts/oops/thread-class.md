---
title: "Thread Class"
date: 2025-05-08T21:14:09+05:30
draft: false
tags: ["OOP", "Java", "Threads"]
categories: ["OOPs"]
---

## The Thread Class

The `Thread` class in Java provides a direct way to create and manage threads. It belongs to the `java.lang` package and provides various methods to control thread behavior.

---

### Creating a Thread Using Thread Class

To create a thread using the `Thread` class, extend it and override its `run()` method.

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running.");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start();  // starts the thread
    }
}
````

---

### Important Methods in Thread Class

| Method      | Description                               |
| ----------- | ----------------------------------------- |
| `start()`   | Starts the thread.                        |
| `run()`     | Contains the code executed by the thread. |
| `sleep(ms)` | Puts thread to sleep for specified time.  |
| `join()`    | Waits for a thread to die.                |
| `isAlive()` | Checks if the thread is still running.    |
| `setName()` | Sets the thread’s name.                   |
| `getName()` | Returns the thread’s name.                |

---

### Example with Sleep and Join

```java
class MyThread extends Thread {
    public void run() {
        try {
            Thread.sleep(500);
            System.out.println("Thread " + Thread.currentThread().getName() + " running.");
        } catch (InterruptedException e) {
            System.out.println("Interrupted");
        }
    }
}

public class Main {
    public static void main(String[] args) throws InterruptedException {
        MyThread t1 = new MyThread();
        t1.setName("Worker1");
        t1.start();
        t1.join();  // Waits for t1 to finish
        System.out.println("Main thread finished.");
    }
}
```

---

### Thread Priorities

Java threads have priorities that help the thread scheduler decide when each thread should run.

* Constants: `MIN_PRIORITY` (1), `NORM_PRIORITY` (5), `MAX_PRIORITY` (10)

```java
t1.setPriority(Thread.MAX_PRIORITY);
```

---

### 🔗 Related Notes

* [Runnable Interface]({{< ref "posts/oops/runnable-interface.md" >}})
* [Concurrent Programming]({{< ref "posts/oops/concurrent-programming.md" >}})
* [Exception Handling]({{< ref "posts/oops/exception-handling.md" >}})
