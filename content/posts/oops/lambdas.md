---
title: "Lambdas"
date: 2025-05-08T22:11:10+05:30
draft: false
tags: ["Java", "Lambda", "Functional Programming", "OOP"]
categories: ["OOPs"]
---

## Lambdas

Lambdas in Java are anonymous functions that can be treated as objects and passed around. Introduced in Java 8, they enable functional programming features such as concise function representations and behavior passing.

---

### Syntax

```java
(parameters) -> expression
(parameters) -> { statements }
````

---

### Example

```java
interface Greeting {
    void sayHello();
}

public class Main {
    public static void main(String[] args) {
        Greeting g = () -> System.out.println("Hello, Lambda!");
        g.sayHello();
    }
}
```

---

### With Parameters

```java
interface MathOperation {
    int operation(int a, int b);
}

public class Main {
    public static void main(String[] args) {
        MathOperation add = (a, b) -> a + b;
        System.out.println(add.operation(5, 3)); // Output: 8
    }
}
```

---

### Use with Collections

```java
List<String> list = Arrays.asList("A", "B", "C");
list.forEach(item -> System.out.println(item));
```

---

### Benefits

* Shorter code
* Improved readability
* Enables functional-style programming

---

### 🔗 Related Notes

* [Functional Interfaces]({{< ref "posts/oops/functional-interfaces.md" >}})
* [Generic Methods]({{< ref "posts/oops/generic-methods.md" >}})

