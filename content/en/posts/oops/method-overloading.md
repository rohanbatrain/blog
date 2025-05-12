---
title: "Method Overloading"
date: 2025-05-08T20:03:35+05:30
draft: false
tags: ["OOP", "Java", "Method Overloading"]
categories: ["OOPs"]
---

## Method Overloading

Method overloading in Java refers to the ability to define multiple methods with the same name but different parameter lists. Overloading is resolved at compile time, and the appropriate method is selected based on the number and type of arguments passed.

### Key Points:
- Overloading is related to the method signature (name and parameters).
- Return type alone cannot be used to overload methods.
- It improves code readability and allows the same method to perform different tasks.

### Example of Method Overloading:
```java
class Calculator {
    // Overloaded method to add two integers
    public int add(int a, int b) {
        return a + b;
    }

    // Overloaded method to add three integers
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // Overloaded method to add two double numbers
    public double add(double a, double b) {
        return a + b;
    }
}
```

### Example of Method Overloading with Different Return Types:

```java
class MathOperation {
    // Method to add two integers
    int add(int a, int b) {
        return a + b;
    }

    // Method to add three integers
    int add(int a, int b, int c) {
        return a + b + c;
    }

    // Method to add two double values
    double add(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        MathOperation math = new MathOperation();

        System.out.println("Sum of two integers: " + math.add(5, 10));            // Output: 15
        System.out.println("Sum of three integers: " + math.add(5, 10, 15));       // Output: 30
        System.out.println("Sum of two doubles: " + math.add(5.5, 10.5));         // Output: 16.0
    }
}
```

### 🔗 Related Notes

* [Access Modifiers]({{< ref "posts/oops/access-modifiers.md" >}})
* [Static Keyword]({{< ref "posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Abstract Classes]({{< ref "posts/oops/abstract-classes.md" >}})
* [Packages and Interfaces]({{< ref "posts/oops/packages-and-interfaces.md" >}})

