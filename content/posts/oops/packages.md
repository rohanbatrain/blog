---
title: "Packages"
date: 2025-05-08T20:15:15+05:30
draft: false
tags: ["OOP", "Java", "Packages"]
categories: ["OOPs"]
---

## Packages

In Java, a **package** is a namespace used to organize classes and interfaces. Packages help avoid name conflicts and make it easier to locate and use classes and interfaces.

### Types of Packages:
1. **Built-in Packages**: These are provided by Java. Examples include:
   - `java.util`
   - `java.io`
   - `java.math`
   
2. **User-defined Packages**: These are created by developers to organize their own classes.

### Example of Creating and Using Packages:
#### Creating a package:
```java
package com.example.animals;

class Dog {
    void bark() {
        System.out.println("Barking...");
    }
}
```

#### Using a class from a package:

```java
import com.example.animals.Dog;

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.bark();  // Output: Barking...
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
