---
title: "Method Overriding"
date: 2025-05-08T20:08:54+05:30
draft: false
tags: ["OOP", "Java", "Method Overriding"]
categories: ["OOPs"]
---

## Method Overriding

Method overriding is an OOP concept where a subclass provides a specific implementation for a method that is already defined in its superclass. The method in the subclass must have the same signature (name, return type, and parameters) as the one in the parent class.

### Key Points:
- Overriding is used to define a new behavior in the subclass for a method inherited from the superclass.
- The method in the subclass must have the same method signature as the one in the parent class.
- The `@Override` annotation is used to indicate that a method is being overridden.
- The method in the parent class must be accessible (i.e., not private).

### Example:
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    // Method overriding
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        myAnimal.sound();  // Output: Animal makes a sound

        Animal myDog = new Dog();
        myDog.sound();  // Output: Dog barks
    }
}
```

### Example with `@Override` annotation:

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        animal.sound();  // Output: Animal makes a sound

        Dog dog = new Dog();
        dog.sound();  // Output: Dog barks
    }
}
```

### 🔗 Related Notes

* [Access Modifiers]({{< ref "en/posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "en/posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "en/posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "en/posts/oops/inheritance.md" >}})
* [Types of Inheritance]({{< ref "en/posts/oops/types-of-inheritance.md" >}})
* [super to Access Superclass Members]({{< ref "en/posts/oops/super-to-access-superclass-members.md" >}})
