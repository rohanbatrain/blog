---
title: "Types of Inheritance"
date: 2025-05-08T20:07:37+05:30
draft: false
tags: ["OOP", "Java", "Types of Inheritance"]
categories: ["OOPs"]
---

## Types of Inheritance

In Java, inheritance allows one class to inherit the attributes and behaviors (fields and methods) of another. There are several types of inheritance, each with its own characteristics and applications in object-oriented programming.

### 1. **Single Inheritance**
In single inheritance, a class inherits from only one parent class. This is the simplest form of inheritance.

### Example:
```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();  // Inherited method from Animal
        dog.bark(); // Method specific to Dog
    }
}
````

### 2. **Multilevel Inheritance**

In multilevel inheritance, a class can inherit from another class, which itself is a subclass of another class. This forms a chain of inheritance.

### Example:

```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

class Puppy extends Dog {
    void play() {
        System.out.println("Playing...");
    }
}

public class Main {
    public static void main(String[] args) {
        Puppy puppy = new Puppy();
        puppy.eat();   // Inherited from Animal
        puppy.bark();  // Inherited from Dog
        puppy.play();  // Specific to Puppy
    }
}
```

### 3. **Hierarchical Inheritance**

In hierarchical inheritance, multiple subclasses inherit from a single parent class. All the subclasses share the same parent class.

### Example:

```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

class Cat extends Animal {
    void meow() {
        System.out.println("Meowing...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();  // Inherited from Animal
        dog.bark(); // Specific to Dog

        Cat cat = new Cat();
        cat.eat();  // Inherited from Animal
        cat.meow(); // Specific to Cat
    }
}
```

### 4. **Multiple Inheritance (Through Interfaces)**

Java does not support multiple inheritance through classes to avoid ambiguity. However, multiple inheritance can be achieved through interfaces, where a class can implement multiple interfaces.

### Example:

```java
interface Animal {
    void eat();
}

interface Mammal {
    void giveBirth();
}

class Dog implements Animal, Mammal {
    public void eat() {
        System.out.println("Eating...");
    }

    public void giveBirth() {
        System.out.println("Giving birth...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();        // Implemented from Animal interface
        dog.giveBirth();  // Implemented from Mammal interface
    }
}
```

### 🔗 Related Notes

* [Access Modifiers]({{< ref "posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Abstract Classes]({{< ref "posts/oops/abstract-classes.md" >}})
* [Packages and Interfaces]({{< ref "posts/oops/packages-and-interfaces.md" >}})

