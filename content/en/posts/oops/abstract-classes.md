---
title: "Abstract Classes"
date: 2025-05-08T20:09:29+05:30
draft: false
tags: ["OOP", "Java", "Abstract Classes"]
categories: ["OOPs"]
---

## Abstract Classes

An **abstract class** in Java is a class that cannot be instantiated on its own and must be subclassed by another class. It is used to provide a common interface for other classes to implement. An abstract class may contain abstract methods (without implementation) and concrete methods (with implementation).

### Key Points:
- An abstract class can have abstract methods (methods without body) and concrete methods (methods with body).
- A subclass that extends an abstract class must provide concrete implementations for all abstract methods.
- An abstract class can have fields, constructors, and methods just like regular classes.
- Abstract methods in an abstract class must be implemented by the subclass unless the subclass is also abstract.

### Example:
```java
abstract class Animal {
    // Abstract method (does not have a body)
    abstract void sound();

    // Regular method
    void sleep() {
        System.out.println("Sleeping...");
    }
}

class Dog extends Animal {
    // Implementing the abstract method
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        // Animal animal = new Animal();  // This will give an error because Animal is abstract
        Dog dog = new Dog();
        dog.sound();  // Output: Dog barks
        dog.sleep();  // Output: Sleeping...
    }
}
```

### Example with multiple abstract methods:

```java
abstract class Shape {
    // Abstract method (no body)
    abstract void draw();
    abstract double area();
}

class Circle extends Shape {
    double radius;

    Circle(double radius) {
        this.radius = radius;
    }

    // Implementing abstract methods
    void draw() {
        System.out.println("Drawing a circle");
    }

    double area() {
        return Math.PI * radius * radius;
    }
}

public class Main {
    public static void main(String[] args) {
        Shape shape = new Circle(5.0);
        shape.draw();  // Output: Drawing a circle
        System.out.println("Area: " + shape.area());  // Output: Area: 78.53981633974483
    }
}
```

### 🔗 Related Notes

* [Access Modifiers]({{< ref "posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Types of Inheritance]({{< ref "posts/oops/types-of-inheritance.md" >}})
* [Method Overriding]({{< ref "posts/oops/method-overriding.md" >}})
* [super to Access Superclass Members]({{< ref "posts/oops/super-to-access-superclass-members.md" >}})
