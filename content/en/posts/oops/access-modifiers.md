---
title: "Access Modifiers"
date: 2025-05-08T20:02:23+05:30
draft: false
tags: ["OOP", "Java", "Access Modifiers"]
categories: ["OOPs"]
---

## Access Modifiers

Access modifiers are keywords in Java that set the visibility and accessibility of classes, methods, and variables. They define the scope of the class members and control how and where they can be accessed. Java provides four types of access modifiers:

### 1. **Public**
The `public` modifier allows the member to be accessed from anywhere in the program, regardless of the package.

### 2. **Private**
The `private` modifier restricts the member to be accessed only within the same class. It cannot be accessed from outside the class, even by subclass objects.

### 3. **Protected**
The `protected` modifier allows access to the member within the same package or by subclasses (even if they are in different packages).

### 4. **Default (Package-Private)**
If no access modifier is specified, the default modifier is applied. The member can be accessed only within the same package.

### Example:
```java
class MyClass {
    public int publicVar;
    private int privateVar;
    protected int protectedVar;
    int defaultVar; // default access modifier

    public void display() {
        System.out.println("Public: " + publicVar);
        System.out.println("Private: " + privateVar);
        System.out.println("Protected: " + protectedVar);
        System.out.println("Default: " + defaultVar);
    }
}
```

### 🔗 Related Notes

* [Method Overloading]({{< ref "en/posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "en/posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "en/posts/oops/inheritance.md" >}})
* [Abstract Classes]({{< ref "en/posts/oops/abstract-classes.md" >}})
* [Packages and Interfaces]({{< ref "en/posts/oops/packages-and-interfaces.md" >}})
