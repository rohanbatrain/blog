---
title: "Generic Class"
date: 2025-05-08T22:06:38+05:30
draft: false
tags: ["Java", "Generics", "OOP"]
categories: ["OOPs"]
---

## Generic Class

A **Generic Class** allows the definition of classes with a placeholder for a type, enabling reusability and type safety. The type is specified when the object is instantiated.

---

### Syntax

```java
class Box<T> {
    T item;
    void set(T item) { this.item = item; }
    T get() { return item; }
}
````

---

### Usage

```java
public class Main {
    public static void main(String[] args) {
        Box<Integer> intBox = new Box<>();
        intBox.set(100);
        System.out.println("Integer Value: " + intBox.get());

        Box<String> strBox = new Box<>();
        strBox.set("Hello Generics");
        System.out.println("String Value: " + strBox.get());
    }
}
```

---

### Multiple Type Parameters

```java
class Pair<K, V> {
    K key;
    V value;

    Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }

    K getKey() { return key; }
    V getValue() { return value; }
}
```

---

### Benefits

* Reduces code duplication
* Type-safe data structures
* Easier to debug and maintain

---

### 🔗 Related Notes

* [Generics Fundamentals]({{< ref "posts/oops/generics-fundamentals.md" >}})
* [Generic Methods]({{< ref "posts/oops/generic-methods.md" >}})
