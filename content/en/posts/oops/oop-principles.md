---
date: 2025-05-08T18:43:59+05:30
title: "Object Oriented Programming Principles"
draft: false
tags: ["OOP", "Principles", "Java"]
categories: ["OOPs"]
---

## 🧠 Object Oriented Programming Principles

Object-Oriented Programming (OOP) is based on **four core principles** that guide how we design software around real-world objects.

---

### 🔑 The Four Core Principles

1. **[Encapsulation]({{< ref "posts/oops/encapsulation.md" >}})**  
   Hides internal details and exposes only what’s necessary.

2. **[Inheritance]({{< ref "posts/oops/inheritance.md" >}})**  
   Allows a class to inherit methods and properties from another class.

3. **[Polymorphism]({{< ref "posts/oops/polymorphism.md" >}})**  
   Enables a single interface to operate on different types.

4. **[Abstraction]({{< ref "posts/oops/abstraction.md" >}})**  
   Focuses on essential characteristics, hiding implementation.

---

### 🎯 Goals of These Principles

- Improve modularity
- Enhance code reuse
- Simplify maintenance
- Align software design with real-world modeling

---

### 🧪 Java in Action

```java
interface Vehicle {
    void start();
}

class Car implements Vehicle {
    public void start() {
        System.out.println("Car started");
    }
}
```

This example combines:

* Abstraction (interface)
* Inheritance (implements)
* Polymorphism (Vehicle reference to Car)
* Encapsulation (internal logic hidden)

---

### 🔗 Related Notes

- [History and Evolution]({{< ref "posts/oops/history-and-evolution.md" >}})
- [Encapsulation]({{< ref "posts/oops/encapsulation.md" >}})
- [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
- [Polymorphism]({{< ref "posts/oops/polymorphism.md" >}})
- [Abstraction]({{< ref "posts/oops/abstraction.md" >}})
