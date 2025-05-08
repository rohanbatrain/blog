---
title: "Generic Methods"
date: 2025-05-08T22:09:12+05:30
draft: false
tags: ["Java", "Generics", "OOP"]
categories: ["OOPs"]
---

## Generic Methods

A **Generic Method** defines a method that operates on objects of various types while providing compile-time type safety. These methods can be used inside generic and non-generic classes.

---

### Syntax

```java
public <T> void printArray(T[] array) {
    for (T element : array) {
        System.out.println(element);
    }
}
```

* `<T>` before the return type indicates the method is generic.
* `T` is the type parameter used within the method.

---

### Example

```java
public class Main {
    public static <T> void display(T[] items) {
        for (T item : items) {
            System.out.print(item + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Integer[] intArray = {1, 2, 3};
        String[] strArray = {"A", "B", "C"};

        display(intArray);
        display(strArray);
    }
}
```

---

### Bounded Type Parameters

Generic methods can restrict the types they accept using bounds.

```java
public <T extends Number> void printNumber(T num) {
    System.out.println(num);
}
```

---

### 🔗 Related Notes

* [Generics Fundamentals]({{< ref "posts/oops/generics-fundamentals.md" >}})
* [Generic Class]({{< ref "posts/oops/generic-class.md" >}})
* [Functional Interfaces]({{< ref "posts/oops/functional-interfaces.md" >}})
