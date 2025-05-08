---
title: "Functional Interfaces"
date: 2025-05-08T22:11:53+05:30
draft: false
tags: ["Java", "Lambda", "Functional Interfaces", "OOP"]
categories: ["OOPs"]
---

## Functional Interfaces

A **Functional Interface** is an interface with exactly one abstract method. It forms the foundation for lambda expressions in Java.

---

### Declaration

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void execute();
}
````

* The `@FunctionalInterface` annotation is optional but recommended.
* Having more than one abstract method will result in a compilation error if the annotation is present.

---

### Example with Lambda

```java
public class Main {
    public static void main(String[] args) {
        MyFunctionalInterface f = () -> System.out.println("Executed!");
        f.execute();
    }
}
```

---

### Built-in Functional Interfaces (in `java.util.function`)

* `Predicate<T>` – returns boolean
* `Function<T, R>` – returns a value
* `Consumer<T>` – performs an action
* `Supplier<T>` – provides a value

```java
Predicate<String> isLong = s -> s.length() > 5;
System.out.println(isLong.test("Hello")); // false
```

---

### Benefits

* Enables cleaner, more modular code
* Essential for lambda expressions
* Supports functional programming

---

### 🔗 Related Notes

* [Lambdas]({{< ref "posts/oops/lambdas.md" >}})
* [Generic Methods]({{< ref "posts/oops/generic-methods.md" >}})
