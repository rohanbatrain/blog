---
title: "Static Keyword"
date: 2025-05-08T20:04:38+05:30
draft: false
tags: ["OOP", "Java", "Static Keyword"]
categories: ["OOPs"]
---

## Static Keyword

The `static` keyword in Java is used to indicate that a particular member (variable, method, or inner class) belongs to the class itself, rather than to instances of the class. It can be applied to variables, methods, blocks, and nested classes.

### Key Points:
- **Static variables** are shared among all instances of the class. They can be accessed without creating an instance of the class.
- **Static methods** can be called without creating an instance of the class and can only access static variables and methods.
- **Static blocks** are used for static initializations and are executed when the class is loaded into memory.

### Example:
```java
class Counter {
    static int count = 0;

    // Static method to increment the count
    public static void increment() {
        count++;
    }

    // Static method to display the count
    public static void displayCount() {
        System.out.println("Count: " + count);
    }
}

public class Main {
    public static void main(String[] args) {
        Counter.increment();
        Counter.increment();
        Counter.displayCount();  // Output: Count: 2
    }
}
````

### 🔗 Related Notes

* [Access Modifiers]({{< ref "posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "posts/oops/method-overloading.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Abstract Classes]({{< ref "posts/oops/abstract-classes.md" >}})
* [Packages and Interfaces]({{< ref "posts/oops/packages-and-interfaces.md" >}})

