---
title: "Layout Managers"
date: 2025-05-08T22:17:28+05:30
draft: false
tags: ["Java", "Swing", "GUI", "Layout", "OOP"]
categories: ["OOPs"]
---

## Layout Managers

**Layout Managers** in Java Swing control the positioning and sizing of components within a container. They help in creating consistent GUI designs that adjust gracefully to different screen sizes.

---

### Common Layout Managers

#### 1. **FlowLayout** (default for JPanel)

Places components in a row, wraps to the next row when full.

```java
setLayout(new FlowLayout());
```

#### 2. **BorderLayout** (default for JFrame)

Divides the container into five regions: NORTH, SOUTH, EAST, WEST, CENTER.

```java
setLayout(new BorderLayout());
add(new JButton("North"), BorderLayout.NORTH);
```

#### 3. **GridLayout**

Places components in a grid with equal-sized cells.

```java
setLayout(new GridLayout(2, 3)); // 2 rows, 3 columns
```

#### 4. **BoxLayout**

Arranges components either vertically or horizontally.

```java
setLayout(new BoxLayout(getContentPane(), BoxLayout.Y_AXIS));
```

---

### Nesting Layouts

You can use multiple panels with different layouts to build complex GUIs.

```java
JPanel topPanel = new JPanel(new FlowLayout());
JPanel centerPanel = new JPanel(new GridLayout(2, 2));
```

---

### 🔗 Related Notes

* [Swing]({{< ref "en/posts/oops/swing.md" >}})
* [Components and Containers]({{< ref "en/posts/oops/components-and-containers.md" >}})
* [Swing Controls]({{< ref "en/posts/oops/swing-controls.md" >}})
