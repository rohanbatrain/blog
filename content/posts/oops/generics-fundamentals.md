---
title: "Generics Fundamentals"
date: 2025-05-08T22:04:00+05:30
draft: false
tags: ["Java", "Generics", "OOP"]
categories: ["OOPs"]
---

## Generics Fundamentals

Generics in Java provide a way to define classes, interfaces, and methods with a placeholder for types. They allow for type safety and code reusability without the need for casting.

---

### Why Generics?

- **Type Safety**: Compile-time checking prevents runtime `ClassCastException`.
- **Code Reusability**: One class or method works with different types.
- **Eliminates Casting**: Reduces boilerplate casting code.

---

### Example Without Generics

```java
ArrayList list = new ArrayList();
list.add("Hello");
String s = (String) list.get(0); // requires casting
````

---

### Example With Generics

```java
ArrayList<String> list = new ArrayList<>();
list.add("Hello");
String s = list.get(0); // no casting required
```

---

### Generic Syntax

```java
class Box<T> {
    T item;
    void set(T item) { this.item = item; }
    T get() { return item; }
}
```

---

### Benefits

* Prevents runtime errors
* More readable and maintainable code
* Encourages clean APIs

---

### 🔗 Related Notes

* [Generic Class]({{< ref "posts/oops/generic-class.md" >}})
* [Generic Methods]({{< ref "posts/oops/generic-methods.md" >}})
* [Functional Interfaces]({{< ref "posts/oops/functional-interfaces.md" >}})
