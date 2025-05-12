---
title: "Interfaces"
date: 2025-05-08T20:15:42+05:30
draft: false
tags: ["OOP", "Java", "Interfaces"]
categories: ["OOPs"]
---

## Interfaces

An **interface** in Java is a reference type, similar to a class, that can contain only constants, method signatures, default methods, static methods, and nested types. Interfaces define a contract that classes must implement.

### Key Points:
- A class can implement multiple interfaces.
- Interfaces provide a way to achieve **abstraction** by allowing methods to be declared without providing their implementation.
- An interface can be used to define common behaviors that multiple classes can share.

### Example of Defining and Implementing an Interface:
#### Defining an interface:
```java
interface Animal {
    void sound();
}
```

#### Implementing the interface in a class:

```java
class Dog implements Animal {
    @Override
    public void sound() {
        System.out.println("Bark");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Dog();
        dog.sound();  // Output: Bark
    }
}
```

### Example with Multiple Interfaces:

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

* [Access Modifiers]({{< ref "en/posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "en/posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "en/posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "en/posts/oops/inheritance.md" >}})
* [Types of Inheritance]({{< ref "en/posts/oops/types-of-inheritance.md" >}})
* [Method Overriding]({{< ref "en/posts/oops/method-overriding.md" >}})

