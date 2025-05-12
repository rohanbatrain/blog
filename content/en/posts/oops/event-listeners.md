---
title: "Event Listeners"
date: 2025-05-08T22:20:16+05:30
draft: false
tags: ["Java", "Swing", "Event Listeners", "GUI", "OOP"]
categories: ["OOPs"]
---

## Event Listeners

**Event Listeners** are interfaces in Java Swing that define methods for responding to user actions or events. Components generate events, and listeners handle them.

---

### Commonly Used Listener Interfaces

| Listener Interface     | Description                           | Method Signature                                  |
|------------------------|---------------------------------------|---------------------------------------------------|
| `ActionListener`       | For button clicks and similar actions | `void actionPerformed(ActionEvent e)`            |
| `MouseListener`        | Mouse click, enter, exit, etc.        | `void mouseClicked(MouseEvent e)` (and others)   |
| `KeyListener`          | Keyboard key press and release        | `void keyPressed(KeyEvent e)` (and others)       |
| `WindowListener`       | Window open, close, minimize, etc.    | `void windowClosing(WindowEvent e)` (and others) |

---

### Example: `ActionListener`

```java
button.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.out.println("Action performed!");
    }
});
```

---

### Example: `MouseListener`

```java
label.addMouseListener(new MouseAdapter() {
    public void mouseClicked(MouseEvent e) {
        System.out.println("Mouse clicked!");
    }
});
```

> `MouseAdapter` is an abstract adapter class that lets you override only the needed methods.

---

### 🔗 Related Notes

* [Swing Event Handling]({{< ref "en/posts/oops/swing-event-handling.md" >}})
* [Event Classes and Listener Interfaces]({{< ref "en/posts/oops/event-classes-and-listener-interfaces.md" >}})
* [Swing Controls]({{< ref "en/posts/oops/swing-controls.md" >}})
