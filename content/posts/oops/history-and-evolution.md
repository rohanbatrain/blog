---
date: 2025-05-08T18:35:36+05:30
title: "Object Oriented Programming - History and Evolution"
draft: false
tags: ["OOP", "History", "Programming Paradigms"]
categories: ["OOPs"]
---

## 🕰️ Object Oriented Programming – History and Evolution

Object-Oriented Programming (OOP) emerged to tackle the increasing complexity of software systems. It provides a structured way to organize code around **objects**, which combine data and behavior.

---

### 📅 Timeline of OOP Evolution

- **1960s – Simula (Norway)**  
  Introduced classes and objects — the foundation of OOP.

- **1970s – Smalltalk**  
  Fully object-oriented; introduced message passing.

- **1980s – C++**  
  Extended C with classes, encapsulation, and inheritance.

- **1995 – Java**  
  Platform-independent language with garbage collection and built-in support for OOP.

---

### 🤔 Why OOP?

Traditional procedural programming (like C) worked fine for small programs but failed to scale well:

- Code was hard to maintain and extend
- Data and logic were separated
- Reuse was limited and error-prone

OOP addressed these issues using four main principles:
[Encapsulation]({{< ref "posts/oops/encapsulation.md" >}}), 
[Inheritance]({{< ref "posts/oops/inheritance.md" >}}), 
[Polymorphism]({{< ref "posts/oops/polymorphism.md" >}}), and 
[Abstraction]({{< ref "posts/oops/abstraction.md" >}}).

---

### 🧪 Simple Java Example

```java
class Car {
    String color = "Red";

    void displayColor() {
        System.out.println("Car color is: " + color);
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.displayColor();
    }
}
```

---

### 🔗 Linked Notes

* [Encapsulation]({{< ref "posts/oops/encapsulation.md" >}})
* [OOP Principles]({{< ref "posts/oops/oop-principles.md" >}})



### 🔗 Related Notes
* [OOPs Principles]({{< ref "posts/oops/oops-principles.md" >}})
* [Encapsulation]({{< ref "posts/oops/encapsulation.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Polymorphism]({{< ref "posts/oops/polymorphism.md" >}})
* [Abstraction]({{< ref "posts/oops/abstraction.md" >}})
* [Features of Java]({{< ref "posts/oops/features-of-java.md" >}})
