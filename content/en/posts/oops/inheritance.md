---
title: "Inheritance"
date: 2025-05-08T20:06:09+05:30
draft: false
tags: ["OOP", "Java", "Inheritance"]
categories: ["OOPs"]
---

## Inheritance

Inheritance is a fundamental concept in Object-Oriented Programming (OOP) that allows one class (child or subclass) to inherit the fields and methods of another class (parent or superclass). This promotes code reusability and allows for hierarchical class relationships.

### Key Points:
- The child class can extend the functionality of the parent class.
- The child class can access public and protected members of the parent class.
- In Java, the `extends` keyword is used to create a subclass.

### Types of Inheritance:
1. **Single Inheritance**: A subclass inherits from one parent class.
2. **Multilevel Inheritance**: A subclass inherits from a parent class, and that parent class can be further extended.
3. **Hierarchical Inheritance**: Multiple subclasses inherit from a single parent class.
4. **Multiple Inheritance (through interfaces)**: Java does not support multiple inheritance through classes, but it can be achieved through interfaces.

### Example:
```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();  // Inherited method
        dog.bark(); // Method of Dog class
    }
}
```

### 🔗 Related Notes

* [Access Modifiers]({{< ref "posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "posts/oops/static-keyword.md" >}})
* [Abstract Classes]({{< ref "posts/oops/abstract-classes.md" >}})
* [Packages and Interfaces]({{< ref "posts/oops/packages-and-interfaces.md" >}})
