---
title: "Types of Nested Classes"
date: 2025-05-08T21:07:55+05:30
draft: false
tags: ["OOP", "Java", "Nested Classes"]
categories: ["OOPs"]
---

## Types of Nested Classes

Java supports four types of nested classes. Each type serves different use cases and has unique access rules.

### 1. Static Nested Class
- Defined using the `static` keyword inside another class.
- Can access only static members of the outer class.
- Does not require an instance of the outer class to be instantiated.

```java
class Outer {
    static int value = 10;

    static class StaticNested {
        void show() {
            System.out.println("Value: " + value);
        }
    }
}
````

**Usage:**

```java
Outer.StaticNested obj = new Outer.StaticNested();
obj.show();
```

---

### 2. Non-static Inner Class

* Defined without `static` keyword.
* Has access to all (including private) members of the outer class.
* Requires an instance of the outer class to be instantiated.

```java
class Outer {
    int value = 20;

    class Inner {
        void show() {
            System.out.println("Value: " + value);
        }
    }
}
```

**Usage:**

```java
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
inner.show();
```

---

### 3. Local Inner Class

* Defined inside a method or a block.
* Can access local variables marked as `final` or effectively final.
* Mostly used for logical grouping or helper purposes.

```java
class Outer {
    void display() {
        int num = 30;

        class LocalInner {
            void show() {
                System.out.println("Number: " + num);
            }
        }

        LocalInner inner = new LocalInner();
        inner.show();
    }
}
```

---

### 4. Anonymous Inner Class

* Declared and instantiated in one statement.
* Has no name.
* Mostly used for implementing interfaces or abstract classes on the fly.

```java
abstract class Animal {
    abstract void sound();
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Animal() {
            void sound() {
                System.out.println("Bark");
            }
        };
        dog.sound();
    }
}
```

### 🔗 Related Notes

* [Nested Classes]({{< ref "posts/oops/nested-classes.md" >}})
* [Runnable Interface]({{< ref "posts/oops/runnable-interface.md" >}})
* [Thread Class]({{< ref "posts/oops/thread-class.md" >}})
