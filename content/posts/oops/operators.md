---
title: "Operators"
date: 2025-05-08T19:01:23+05:30
draft: false
tags: ["Java", "Operators"]
categories: ["Unit I", "OOPs"]
---

## ➗ Operators in Java

In Java, **operators** are special symbols used to perform operations on variables and values. Java has a rich set of operators that can be categorized into several types.

---

### 🧮 Types of Operators in Java

1. **Arithmetic Operators**
   - `+`, `-`, `*`, `/`, `%`
   - Used to perform mathematical operations.

2. **Relational Operators**
   - `==`, `!=`, `>`, `<`, `>=`, `<=`
   - Used to compare two values.

3. **Logical Operators**
   - `&&`, `||`, `!`
   - Used to perform logical operations (AND, OR, NOT).

4. **Assignment Operators**
   - `=`, `+=`, `-=`, `*=`, `/=`
   - Used to assign values to variables.

5. **Unary Operators**
   - `+`, `-`, `++`, `--`, `!`
   - Used to perform operations on a single operand.

6. **Bitwise Operators**
   - `&`, `|`, `^`, `<<`, `>>`
   - Used to perform bit-level operations.

7. **Ternary Operator**
   - `condition ? expression1 : expression2`
   - A shorthand for `if-else` statement.

8. **Instanceof Operator**
   - Used to check if an object is an instance of a specific class.

---

### 🧪 Example: Arithmetic and Relational Operators

```java
public class OperatorsExample {
    public static void main(String[] args) {
        int a = 10, b = 5;
        System.out.println("Addition: " + (a + b));    // 15
        System.out.println("Subtraction: " + (a - b)); // 5
        System.out.println("Is a > b? " + (a > b));    // true
    }
}
````

---

### ⚙️ Operator Precedence

Operator precedence determines the order in which operators are evaluated. For example, multiplication and division have higher precedence than addition and subtraction.

---


### 🔗 Related Notes
* [Data Types]({{< ref "posts/oops/data-types.md" >}})
* [Variables]({{< ref "posts/oops/variables.md" >}})
* [Program Control Statements]({{< ref "posts/oops/program-control-statements.md" >}})
* [Arrays]({{< ref "posts/oops/arrays.md" >}})
* [Strings]({{< ref "posts/oops/strings.md" >}})
