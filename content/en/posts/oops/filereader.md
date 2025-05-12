---
title: "Filereader"
date: 2025-05-08T21:18:57+05:30
draft: false
tags: ["OOP", "Java", "IO"]
categories: ["OOPs"]
---

## FileReader

The `FileReader` class in Java is used to read character-based data from files. It is part of the `java.io` package and is ideal for reading text files.

---

### Basic Example

```java
import java.io.FileReader;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try {
            FileReader reader = new FileReader("example.txt");
            int character;
            while ((character = reader.read()) != -1) {
                System.out.print((char) character);
            }
            reader.close();
        } catch (IOException e) {
            System.out.println("An error occurred.");
            e.printStackTrace();
        }
    }
}
```

---

### Best Practices

* Always close the `FileReader` to avoid memory leaks.
* Wrap with `BufferedReader` for efficient reading of large files.
* Use `try-with-resources` for automatic closing.

```java
import java.io.*;

public class Main {
    public static void main(String[] args) {
        try (BufferedReader br = new BufferedReader(new FileReader("example.txt"))) {
            String line;
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

---

### 🔗 Related Notes

* [FileWriter]({{< ref "posts/oops/filewriter.md" >}})
* [Exception Handlers]({{< ref "posts/oops/exception-handlers.md" >}})
* [Concurrent Programming]({{< ref "posts/oops/concurrent-programming.md" >}})
