---
title: "Swing"
date: 2025-05-08T22:13:44+05:30
draft: false
tags: ["Java", "Swing", "GUI", "OOP"]
categories: ["OOPs"]
---

## Swing

**Swing** is a part of Java Foundation Classes (JFC) used to create **Graphical User Interfaces (GUIs)**. It builds on AWT (Abstract Window Toolkit) but provides a richer set of components and is more flexible.

---

### Key Features

- **Lightweight Components** (do not rely on native OS peers)
- **Pluggable Look-and-Feel**
- **MVC Architecture**
- Highly customizable and extensible

---

### Basic Structure

```java
import javax.swing.*;

public class HelloSwing {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Swing Example");
        JButton button = new JButton("Click Me!");

        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(300, 200);
        frame.add(button);
        frame.setVisible(true);
    }
}
```

---

### Core Components

* `JFrame` – Top-level window
* `JButton` – Push button
* `JLabel` – Display text
* `JTextField` – Single-line input
* `JPanel` – Generic container

---

### Benefits of Swing

* Cross-platform consistency
* Rich component library
* Backed by event-driven programming

---

### 🔗 Related Notes

* [Components and Containers]({{< ref "en/posts/oops/components-and-containers.md" >}})
* [Layout Managers]({{< ref "en/posts/oops/layout-managers.md" >}})
* [Swing Event Handling]({{< ref "en/posts/oops/swing-event-handling.md" >}})
