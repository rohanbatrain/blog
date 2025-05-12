---
title: "Swing Event Handling"
date: 2025-05-08T22:18:04+05:30
draft: false
tags: ["Java", "Swing", "Event Handling", "GUI", "OOP"]
categories: ["OOPs"]
---

## Swing Event Handling

**Event Handling** in Swing is based on the delegation event model, where an **event source** (component) notifies one or more **listeners** when an event occurs.

---

### Key Concepts

- **Event Source**: The component that generates an event (e.g., `JButton`)
- **Event Listener**: An interface that receives and processes the event (e.g., `ActionListener`)
- **Event Object**: Carries information about the event (e.g., `ActionEvent`)

---

### Example: Handling Button Click

```java
import javax.swing.*;
import java.awt.event.*;

public class EventExample {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Event Example");
        JButton button = new JButton("Click Me");

        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                System.out.println("Button clicked!");
            }
        });

        frame.add(button);
        frame.setSize(200, 150);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
```

---

### Lambda Version (Java 8+)

```java
button.addActionListener(e -> System.out.println("Clicked!"));
```

---

### Event Flow

1. User interacts with a component (e.g., clicks a button).
2. Component generates an event object.
3. Event object is passed to the registered listener’s method.

---

### 🔗 Related Notes

* [Event Listeners]({{< ref "posts/oops/event-listeners.md" >}})
* [Event Classes and Listener Interfaces]({{< ref "posts/oops/event-classes-and-listener-interfaces.md" >}})
* [Swing Controls]({{< ref "posts/oops/swing-controls.md" >}})

