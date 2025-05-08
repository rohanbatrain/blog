---
title: "Components and Containers"
date: 2025-05-08T22:16:25+05:30
draft: false
tags: ["Java", "Swing", "GUI", "OOP"]
categories: ["OOPs"]
---

## Components and Containers

In Swing, **Components** are the visual elements like buttons, labels, and text fields, while **Containers** hold and organize these components.

---

### Components

Components are instances of classes that inherit from `java.awt.Component`. Common examples include:

- `JButton`
- `JLabel`
- `JTextField`
- `JCheckBox`
- `JComboBox`

```java
JButton button = new JButton("Click Me");
JLabel label = new JLabel("Hello");
````

---

### Containers

Containers are components that can hold other components (including other containers). Examples:

* `JFrame` – Top-level window
* `JPanel` – Generic lightweight container
* `JDialog` – Dialog window

```java
JPanel panel = new JPanel();
panel.add(button);
frame.add(panel);
```

---

### Nesting Components

You can nest components within containers to create structured layouts.

```java
JPanel panel = new JPanel();
panel.add(new JLabel("Name:"));
panel.add(new JTextField(10));
```

---

### 🔗 Related Notes

* [Swing]({{< ref "posts/oops/swing.md" >}})
* [Layout Managers]({{< ref "posts/oops/layout-managers.md" >}})
* [Swing Controls]({{< ref "posts/oops/swing-controls.md" >}})
