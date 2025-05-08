---
date: 2025-05-08T18:41:22+05:30
title: "Polymorphism"
draft: false
tags: ["OOP", "Polymorphism", "Java"]
categories: ["Unit I", "OOPs"]
---

## 🔁 Polymorphism

Polymorphism allows **one interface to be used for different underlying forms (data types)**. It enables the same method name to behave differently depending on the context — improving flexibility and maintainability.

---

### 🎯 Types of Polymorphism in Java

1. **Compile-time (Static) Polymorphism**  
   Achieved via **method overloading** — same method name with different parameters.

2. **Runtime (Dynamic) Polymorphism**  
   Achieved via **method overriding** — subclass provides a specific implementation of a method defined in its superclass.

---

### 🧪 Java Example: Compile-time

```java
class MathOps {
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
````

---

### 🧪 Java Example: Runtime

```java
class Animal {
    void makeSound() {
        System.out.println("Some sound...");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Bark");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.makeSound();  // Output: Bark (runtime polymorphism)
    }
}
```

---

### ✅ Advantages

* Flexible and extensible code
* Supports dynamic method resolution
* Key to achieving loose coupling in OOP

---



### 🔗 Related Notes
* [History and Evolution]({{< ref "posts/oops/history-and-evolution.md" >}})
* [OOPs Principles]({{< ref "posts/oops/oops-principles.md" >}})
* [Features of Java]({{< ref "posts/oops/features-of-java.md" >}})
* [Encapsulation]({{< ref "posts/oops/encapsulation.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Abstraction]({{< ref "posts/oops/abstraction.md" >}})
