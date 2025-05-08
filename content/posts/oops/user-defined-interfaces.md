---
title: "User Defined Interfaces"
date: 2025-05-08T20:19:59+05:30
draft: false
tags: ["OOP", "Java", "Interfaces", "User-defined"]
categories: ["OOPs"]
---

## User-defined Interfaces

In Java, **User-defined Interfaces** are interfaces that you create to define a contract that classes must follow. These interfaces allow you to define abstract methods without providing implementations. Classes that implement the interface must provide their own implementations for the abstract methods.

### Key Points:
- A user-defined interface can contain abstract methods (methods without implementations) and constants (static final variables).
- A class that implements a user-defined interface must provide an implementation for all abstract methods in the interface.
- Multiple interfaces can be implemented by a single class.

### Example of User-defined Interface:
#### Defining an Interface:
```java
interface Animal {
    void sound();  // Abstract method
    void move();   // Abstract method
}
```

#### Implementing the Interface in a Class:

```java
class Dog implements Animal {
    @Override
    public void sound() {
        System.out.println("Bark");
    }

    @Override
    public void move() {
        System.out.println("Dog runs");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.sound();  // Output: Bark
        dog.move();   // Output: Dog runs
    }
}
```

### Example of Multiple Interfaces Implementation:

```java
interface Animal {
    void sound();
}

interface Mammal {
    void move();
}

class Dog implements Animal, Mammal {
    @Override
    public void sound() {
        System.out.println("Bark");
    }

    @Override
    public void move() {
        System.out.println("Dog runs");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.sound();  // Output: Bark
        dog.move();   // Output: Dog runs
    }
}
```

### 🔗 Related Notes

* [Packages and Interfaces]({{< ref "posts/oops/packages-and-interfaces.md" >}})
* [Access Modifiers]({{< ref "posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Types of Inheritance]({{< ref "posts/oops/types-of-inheritance.md" >}})
* [Method Overriding]({{< ref "posts/oops/method-overriding.md" >}})
