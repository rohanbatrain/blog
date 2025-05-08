---
title: "Filewriter"
date: 2025-05-08T21:17:47+05:30
draft: false
tags: ["OOP", "Java", "IO"]
categories: ["OOPs"]
---

## FileWriter

The `FileWriter` class in Java is used to write character-based data to files. It is part of the `java.io` package and is generally used for writing text files.

---

### Basic Example

```java
import java.io.FileWriter;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try {
            FileWriter writer = new FileWriter("example.txt");
            writer.write("Hello, FileWriter!");
            writer.close();
            System.out.println("Successfully written to the file.");
        } catch (IOException e) {
            System.out.println("An error occurred.");
            e.printStackTrace();
        }
    }
}
```

---

### Appending to a File

Use the overloaded constructor with `true` to append data.

```java
FileWriter writer = new FileWriter("example.txt", true);
writer.write("\nThis will be appended.");
writer.close();
```

---

### Best Practices

* Always close the `FileWriter` to free resources.
* Wrap with `BufferedWriter` for efficient writing of large data.
* Use `try-with-resources` to auto-close the stream.

```java
try (FileWriter writer = new FileWriter("example.txt")) {
    writer.write("Auto-closed FileWriter.");
}
```

---

### 🔗 Related Notes

* [FileReader]({{< ref "posts/oops/filereader.md" >}})
* [Exception Handlers]({{< ref "posts/oops/exception-handlers.md" >}})
* [Concurrent Programming]({{< ref "posts/oops/concurrent-programming.md" >}})

