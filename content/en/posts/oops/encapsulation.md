---
date: 2025-05-08T18:38:47+05:30
title: "Encapsulation"
draft: false
tags: ["OOP", "Encapsulation", "Java"]
categories: ["OOPs"]
---

## 🔐 Encapsulation

Encapsulation is one of the four core principles of Object-Oriented Programming. It involves **wrapping data and code** that operates on the data into a single unit: the **class**.

---

### 🧩 Key Concepts

- Declaring variables as `private` to prevent direct access from outside.
- Providing `public` methods (getters/setters) to read or modify private variables.
- Helps enforce data protection, validation, and clean APIs.

---

### 📌 Why Use Encapsulation?

- Keeps internal implementation hidden
- Prevents external interference or misuse
- Allows safe and controlled access
- Promotes modularity and maintainability

---

### 🧪 Java Example

```java
class Student {
    private int age;

    // Setter with validation
    public void setAge(int a) {
        if (a > 0) age = a;
    }

    // Getter
    public int getAge() {
        return age;
    }
}
```

---



### 🔗 Related Notes
* [History and Evolution]({{< ref "en/posts/oops/history-and-evolution.md" >}})
* [OOPs Principles]({{< ref "en/posts/oops/oops-principles.md" >}})
* [Features of Java]({{< ref "en/posts/oops/features-of-java.md" >}})
* [Inheritance]({{< ref "en/posts/oops/inheritance.md" >}})
* [Polymorphism]({{< ref "en/posts/oops/polymorphism.md" >}})
* [Abstraction]({{< ref "en/posts/oops/abstraction.md" >}})
