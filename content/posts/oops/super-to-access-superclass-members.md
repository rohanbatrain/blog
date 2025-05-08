---
title: "Super to Access Superclass Members"
date: 2025-05-08T20:08:14+05:30
draft: false
tags: ["OOP", "Java", "super Keyword"]
categories: ["OOPs"]
---

## super to Access Superclass Members

In Java, the `super` keyword refers to the immediate parent class of a given object. It is used to access members (fields, methods, and constructors) of the parent class from the child class. 

### Key Uses of `super`:
1. **Accessing Superclass Methods**: It is used to call a method of the superclass when the subclass has overridden that method.
2. **Accessing Superclass Constructor**: It is used to call the constructor of the superclass from the subclass.
3. **Accessing Superclass Fields**: It allows access to the fields of the superclass.

### Example 1: Using `super` to call a superclass method
```java
class Animal {
    void eat() {
        System.out.println("Animal is eating...");
    }
}

class Dog extends Animal {
    void eat() {
        super.eat();  // Call the eat() method of the parent class Animal
        System.out.println("Dog is eating...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();  // Output will be: Animal is eating... Dog is eating...
    }
}
```

### Example 2: Using `super` to call a superclass constructor

```java
class Animal {
    Animal() {
        System.out.println("Animal constructor");
    }
}

class Dog extends Animal {
    Dog() {
        super();  // Call the constructor of the parent class Animal
        System.out.println("Dog constructor");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();  // Output will be: Animal constructor Dog constructor
    }
}
```

### Example 3: Using `super` to access a superclass field

```java
class Animal {
    String name = "Animal";
}

class Dog extends Animal {
    String name = "Dog";

    void display() {
        System.out.println("Name from Dog class: " + name);
        System.out.println("Name from Animal class: " + super.name);  // Access the name from Animal class
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.display();  // Output will be: Name from Dog class: Dog Name from Animal class: Animal
    }
}
```

### 🔗 Related Notes

* [Access Modifiers]({{< ref "posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Types of Inheritance]({{< ref "posts/oops/types-of-inheritance.md" >}})
* [Abstract Classes]({{< ref "posts/oops/abstract-classes.md" >}})
