---
title: "Variables"
date: 2025-05-08T19:00:08+05:30
draft: false
tags: ["Java", "Variables"]
categories: ["OOPs"]
---

## 📊 Variables in Java

In Java, **variables** are used to store data that can be used later in the program. Each variable has a **data type** and is associated with a **name** that can be used to reference the value it holds.

---

### 🧠 Types of Variables in Java

1. **Instance Variables**  
   - Declared inside a class but outside any method.
   - Associated with an object instance.

2. **Local Variables**  
   - Declared inside a method, constructor, or block.
   - Exist only within the scope of the method/block.

3. **Static Variables (Class Variables)**  
   - Declared with the `static` keyword.
   - Shared among all instances of the class.

4. **Final Variables**  
   - Declared with the `final` keyword.
   - Cannot be changed once assigned a value.

---

### 🧪 Example: Different Types of Variables

```java
public class VariablesExample {
    int instanceVar = 10; // instance variable

    public void exampleMethod() {
        int localVar = 20;  // local variable
        System.out.println("Local Variable: " + localVar);
        System.out.println("Instance Variable: " + instanceVar);
    }

    public static void main(String[] args) {
        VariablesExample obj = new VariablesExample();
        obj.exampleMethod();
    }
}
```

---

### 🚨 Important Notes

* **Default Values**: Variables in Java are assigned default values if not explicitly initialized. For example, `int` defaults to `0`, and `boolean` defaults to `false`.
* **Final Variables**: Once assigned, `final` variables cannot be modified.

---


### 🔗 Related Notes
* [Data Types]({{< ref "en/posts/oops/data-types.md" >}})
* [Operators]({{< ref "en/posts/oops/operators.md" >}})
* [Program Control Statements]({{< ref "en/posts/oops/program-control-statements.md" >}})
* [Arrays]({{< ref "en/posts/oops/arrays.md" >}})
* [Strings]({{< ref "en/posts/oops/strings.md" >}})
