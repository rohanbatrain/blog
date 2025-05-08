---
title: "Abstraction"
date: 2025-05-08T18:42:45+05:30
draft: false
tags: ["OOP", "Abstraction", "Java"]
categories: ["OOPs"]
---

## 🧊 Abstraction

**Abstraction** is the process of hiding implementation details and exposing only the essential features. It allows developers to focus on *what* an object does instead of *how* it does it.

---

### 🧱 In Java, Abstraction Is Achieved By:

- **Abstract classes** (`abstract` keyword)
- **Interfaces** (fully abstract)

---

### 🧪 Example Using Abstract Class

```java
abstract class Animal {
    abstract void makeSound();

    void breathe() {
        System.out.println("Breathing...");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Bark");
    }
}
```

---

### 🧪 Example Using Interface

```java
interface Drawable {
    void draw();
}

class Circle implements Drawable {
    public void draw() {
        System.out.println("Drawing Circle");
    }
}
```

---

### ✅ Benefits of Abstraction

* Reduces complexity
* Increases reusability
* Enforces standardization (especially through interfaces)
* Helps in designing scalable and modular systems

---



### 🔗 Related Notes
* [History and Evolution]({{< ref "posts/oops/history-and-evolution.md" >}})
* [OOPs Principles]({{< ref "posts/oops/oops-principles.md" >}})
* [Features of Java]({{< ref "posts/oops/features-of-java.md" >}})
* [Encapsulation]({{< ref "posts/oops/encapsulation.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Polymorphism]({{< ref "posts/oops/polymorphism.md" >}})
