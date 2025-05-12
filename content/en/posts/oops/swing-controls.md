---
title: "Swing Controls"
date: 2025-05-08T22:22:30+05:30
draft: false
tags: ["Java", "Swing", "Controls", "GUI", "OOP"]
categories: ["OOPs"]
---

## Swing Controls

Swing provides a set of **controls** (also known as components) to create interactive user interfaces. These controls are part of the `javax.swing` package and can be easily added to containers like `JPanel` and `JFrame`.

---

### Common Swing Controls

| Control             | Description                                             |
|---------------------|---------------------------------------------------------|
| `JButton`           | Button that triggers an action when clicked.             |
| `JLabel`            | Displays a short string or an image.                     |
| `JTextField`        | A single-line text input field.                         |
| `JTextArea`         | A multi-line text input field.                           |
| `JCheckBox`         | A checkbox for binary choices (checked/unchecked).       |
| `JRadioButton`      | A radio button for selecting one option from a group.    |
| `JComboBox`         | A dropdown menu for selecting from a list of items.      |
| `JList`             | A list that allows selecting one or more items.          |

---

### Example: Using JButton and JLabel

```java
JFrame frame = new JFrame("Swing Controls");
JButton button = new JButton("Click Me");
JLabel label = new JLabel("Hello, World!");

button.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        label.setText("Button Clicked!");
    }
});

frame.add(button, BorderLayout.NORTH);
frame.add(label, BorderLayout.CENTER);
frame.setSize(300, 200);
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
frame.setVisible(true);
```

---

### Example: JCheckBox

```java
JCheckBox checkBox = new JCheckBox("Agree to terms");
checkBox.addItemListener(new ItemListener() {
    public void itemStateChanged(ItemEvent e) {
        if (e.getStateChange() == ItemEvent.SELECTED) {
            System.out.println("Checked");
        } else {
            System.out.println("Unchecked");
        }
    }
});
```

---

### Example: JComboBox

```java
String[] items = { "Java", "Python", "C++", "JavaScript" };
JComboBox<String> comboBox = new JComboBox<>(items);
comboBox.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        String selectedItem = (String) comboBox.getSelectedItem();
        System.out.println("Selected: " + selectedItem);
    }
});
```

---

### 🔗 Related Notes

* [Swing Event Handling]({{< ref "posts/oops/swing-event-handling.md" >}})
* [Event Listeners]({{< ref "posts/oops/event-listeners.md" >}})
* [Swing]({{< ref "posts/oops/swing.md" >}})
