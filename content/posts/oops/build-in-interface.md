---
title: "Build in Interface"
date: 2025-05-08T20:19:14+05:30
draft: false
tags: ["OOP", "Java", "Interfaces", "Built-in"]
categories: ["OOPs"]
---

## Build-in Interface

In Java, **Built-in Interfaces** are interfaces that are part of the Java standard library. These interfaces are provided by Java and can be used directly in your applications without needing to define them yourself.

### Common Built-in Interfaces:
1. **Comparable**: This interface is used to compare objects for sorting. A class that implements `Comparable` must provide an implementation for the `compareTo()` method.
   - Method: `int compareTo(T o)`

2. **Cloneable**: This interface is used to indicate that objects of a class can be cloned using the `clone()` method.
   - Method: `Object clone()`

3. **Serializable**: This interface is used to mark a class whose objects can be serialized, i.e., converted into a byte stream that can be saved to a file or transferred over a network.

4. **Iterable**: This interface is used to represent collections that can be iterated (looped through) using an enhanced for-loop or an iterator.

### Example of Comparable Interface:
```java
import java.util.*;

class Student implements Comparable<Student> {
    int rollNo;
    String name;

    Student(int rollNo, String name) {
        this.rollNo = rollNo;
        this.name = name;
    }

    @Override
    public int compareTo(Student other) {
        return this.rollNo - other.rollNo;  // Sorting based on roll number
    }
}

public class Main {
    public static void main(String[] args) {
        List<Student> students = new ArrayList<>();
        students.add(new Student(101, "John"));
        students.add(new Student(102, "Alice"));
        students.add(new Student(103, "Bob"));

        Collections.sort(students);

        for (Student student : students) {
            System.out.println(student.rollNo + " " + student.name);
        }
    }
}
````

### Example of Cloneable Interface:

```java
class Person implements Cloneable {
    String name;

    Person(String name) {
        this.name = name;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}

public class Main {
    public static void main(String[] args) {
        try {
            Person person1 = new Person("John");
            Person person2 = (Person) person1.clone();

            System.out.println(person1.name);  // Output: John
            System.out.println(person2.name);  // Output: John
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }
    }
}
```

### 🔗 Related Notes

* [Packages and Interfaces]({{< ref "posts/oops/packages-and-interfaces.md" >}})
* [Access Modifiers]({{< ref "posts/oops/access-modifiers.md" >}})
* [Method Overloading]({{< ref "posts/oops/method-overloading.md" >}})
* [Static Keyword]({{< ref "posts/oops/static-keyword.md" >}})
* [Inheritance]({{< ref "posts/oops/inheritance.md" >}})
* [Types of Inheritance]({{< ref "posts/oops/types-of-inheritance.md" >}})
* [Method Overriding]({{< ref "posts/oops/method-overriding.md" >}})

