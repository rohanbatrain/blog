---
title: "Nested Classes"
date: 2025-05-08T21:05:26+05:30
draft: false
tags: ["OOP", "Java", "Nested Classes"]
categories: ["OOPs"]
---

## Nested Classes

A **Nested Class** is a class that is defined within another class. In Java, nested classes can be categorized into several types, such as static nested classes, inner classes, local classes, and anonymous classes.

### Types of Nested Classes:
1. **Static Nested Class**: A nested class that is declared static. It can access the static members of the outer class but cannot access the non-static members.
   - Example:
   ```java
   class Outer {
       static int num = 10;
       static class Inner {
           void display() {
               System.out.println(num);
           }
       }
   }
```

2. **Inner Class (Non-static Nested Class)**: A class that is defined inside another class without the `static` keyword. It can access both static and non-static members of the outer class.

   * Example:

   ```java
   class Outer {
       int num = 10;
       class Inner {
           void display() {
               System.out.println(num);
           }
       }
   }
   ```

3. **Local Inner Class**: A class defined inside a method. It can access the local variables and parameters of the method.

   * Example:

   ```java
   class Outer {
       void method() {
           class Inner {
               void display() {
                   System.out.println("Inside method");
               }
           }
           Inner inner = new Inner();
           inner.display();
       }
   }
   ```

4. **Anonymous Inner Class**: A class without a name, defined at the time of instantiation. It's often used in event handling.

   * Example:

   ```java
   class Outer {
       void method() {
           Runnable r = new Runnable() {
               @Override
               public void run() {
                   System.out.println("Anonymous class");
               }
           };
           r.run();
       }
   }
   ```

### 🔗 Related Notes

* [Exception Handling]({{< ref "posts/oops/exception-handling.md" >}})
* [Types of Nested Classes]({{< ref "posts/oops/types-of-nested-classes.md" >}})
* [The Thread Class]({{< ref "posts/oops/thread-class.md" >}})
* [Runnable Interface]({{< ref "posts/oops/runnable-interface.md" >}})
