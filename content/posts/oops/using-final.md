---
title: "Using Final"
date: 2025-05-08T20:13:02+05:30
draft: false
tags: ["OOP", "Java", "final Keyword"]
categories: ["OOPs"]
---

## Using final

The `final` keyword in Java is used to apply restrictions on classes, methods, and variables. It can be used to prevent inheritance, method overriding, and modification of variables.

### Key Points:
1. **final class**: A class declared as `final` cannot be subclassed.
2. **final method**: A method declared as `final` cannot be overridden by subclasses.
3. **final variable**: A variable declared as `final` cannot be reassigned after initialization.

### Example 1: Using `final` with a class
When a class is declared `final`, it cannot be extended (inherited).

```java
final class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

// The following code will result in a compile-time error
// class Dog extends Animal { }
````

### Example 2: Using `final` with a method

A `final` method cannot be overridden by a subclass.

```java
class Animal {
    final void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    // The following code will result in a compile-time error
    // void sound() {
    //     System.out.println("Dog barks");
    // }
}
```

### Example 3: Using `final` with a variable

A `final` variable can only be initialized once. Once initialized, its value cannot be changed.

```java
class Dog {
    final String name = "Buddy";

    void changeName() {
        // The following line will cause a compile-time error
        // name = "Max";
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        System.out.println(dog.name);  // Output: Buddy
    }
}
```

### Example 4: Using `final` with method parameters

A method parameter can also be declared `final` to prevent modification within the method.

```java
class Animal {
    void setName(final String name) {
        // The following line will cause a compile-time error
        // name = "Buddy";
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
* [Abstract Classes]({{< ref "posts/oops/abstract-classes.md" >}})
