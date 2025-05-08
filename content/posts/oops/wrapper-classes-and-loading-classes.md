---
title: "Wrapper Classes and Loading Classes"
date: 2025-05-08T22:50:46+05:30
draft: false
tags: ["Java", "Wrapper Classes", "Loading Classes", "OOP"]
categories: ["OOPs"]
---

## Wrapper Classes and Loading Classes

In Java, **Wrapper Classes** are used to provide object representations for the primitive data types. These classes allow primitive types to be treated as objects, enabling them to be used in data structures that require objects (like collections). **Loading Classes** refer to the mechanism of dynamically loading classes during runtime using Java's reflection mechanism.

---

### Wrapper Classes

Each primitive type in Java has a corresponding wrapper class. These wrapper classes are part of the `java.lang` package and provide utility methods to convert between primitive types and their object counterparts.

#### List of Wrapper Classes

1. **Integer**: Corresponds to the `int` primitive type.
   - Methods: `parseInt()`, `intValue()`, `compareTo()`, etc.

   ```java
   Integer i = Integer.valueOf(10);
   int x = i.intValue();
```

2. **Double**: Corresponds to the `double` primitive type.

   * Methods: `parseDouble()`, `doubleValue()`, `compareTo()`, etc.

   ```java
   Double d = Double.valueOf(20.5);
   double y = d.doubleValue();
   ```

3. **Character**: Corresponds to the `char` primitive type.

   * Methods: `charValue()`, `compareTo()`, etc.

   ```java
   Character c = Character.valueOf('A');
   char ch = c.charValue();
   ```

4. **Boolean**: Corresponds to the `boolean` primitive type.

   * Methods: `parseBoolean()`, `booleanValue()`, etc.

   ```java
   Boolean b = Boolean.valueOf(true);
   boolean flag = b.booleanValue();
   ```

5. **Long**: Corresponds to the `long` primitive type.

   * Methods: `parseLong()`, `longValue()`, etc.

   ```java
   Long l = Long.valueOf(100L);
   long val = l.longValue();
   ```

6. **Float**: Corresponds to the `float` primitive type.

   * Methods: `parseFloat()`, `floatValue()`, etc.

   ```java
   Float f = Float.valueOf(10.5f);
   float floatValue = f.floatValue();
   ```

7. **Byte**: Corresponds to the `byte` primitive type.

   * Methods: `parseByte()`, `byteValue()`, etc.

   ```java
   Byte b = Byte.valueOf((byte) 10);
   byte byteValue = b.byteValue();
   ```

8. **Short**: Corresponds to the `short` primitive type.

   * Methods: `parseShort()`, `shortValue()`, etc.

   ```java
   Short s = Short.valueOf((short) 5);
   short shortValue = s.shortValue();
   ```

#### Autoboxing and Unboxing

* **Autoboxing**: The automatic conversion between primitive types and their wrapper classes.
* **Unboxing**: The automatic conversion from wrapper classes back to primitive types.

```java
Integer i = 10;  // Autoboxing
int x = i;       // Unboxing
```

---

### Loading Classes

Class loading in Java is the process of loading a class's bytecode into memory so that it can be used by the Java Virtual Machine (JVM). This is done dynamically at runtime, and Java provides the `Class` class and reflection API to load classes.

#### Key Methods for Loading Classes

1. **`Class.forName(String className)`**:

   * Loads a class dynamically at runtime.

   ```java
   Class<?> cls = Class.forName("java.util.ArrayList");
   ```

2. **`getClass()`**:

   * Returns the `Class` object associated with the instance.

   ```java
   String str = "Hello";
   Class<?> cls = str.getClass();
   ```

3. **Reflection API**:

   * Provides methods to inspect and manipulate classes and objects at runtime. You can access constructors, fields, and methods of a class dynamically.

   ```java
   Class<?> cls = Class.forName("java.util.ArrayList");
   Method method = cls.getMethod("add", Object.class);
   ```

4. **`ClassLoader`**:

   * A `ClassLoader` is responsible for loading classes into memory. The JVM uses the system class loader by default, but you can create custom class loaders.

   ```java
   ClassLoader classLoader = ClassLoader.getSystemClassLoader();
   Class<?> cls = classLoader.loadClass("java.util.ArrayList");
   ```

---

### Example: Using Wrapper Classes and Class Loading

```java
public class WrapperClassesExample {
    public static void main(String[] args) throws ClassNotFoundException {
        // Using Wrapper Classes
        Integer integer = Integer.valueOf(100);
        System.out.println("Integer value: " + integer);

        // Autoboxing and Unboxing
        int x = integer;  // Unboxing
        Integer y = 50;    // Autoboxing
        System.out.println("Autoboxed value: " + y);

        // Class Loading
        Class<?> cls = Class.forName("java.util.ArrayList");
        System.out.println("Class loaded: " + cls.getName());
    }
}
```

---

### 🔗 Related Notes

* [Wrapper Classes and Loading Classes]({{< ref "posts/oops/wrapper-classes-and-loading-classes.md" >}})
* [Collections]({{< ref "posts/oops/collections.md" >}})
