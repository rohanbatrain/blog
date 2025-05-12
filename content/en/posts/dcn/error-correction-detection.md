---
date: 2025-05-12T18:18:07+05:30
title: "Character Codes and Error Detection Techniques"
tags: ["data link layer", "error detection", "character encoding", "VRC", "CRC"]
series: "Data Link Layer"
categories: ["Digital Communication and Computer Networks"]
draft: false
---

### 🔤 Character Codes in Communication

Character codes convert symbols into binary so they can be transmitted or stored.

#### Common Character Encodings:
- **ASCII (7-bit):** Standard for English text.
- **Extended ASCII (8-bit):** Includes extra symbols.
- **Unicode (UTF-8):** Multi-language, variable-length encoding.

Character codes are foundational — they are how **meaning is encoded into binary**.

---

### ⚠️ Error Detection Techniques

Communication is susceptible to noise. Error detection techniques help identify if data has been corrupted during transmission.

#### 🧩 Common Redundancy Checking Methods:

- **VRC (Vertical Redundancy Check):**
  - Also called **parity check**.
  - Adds a parity bit (even/odd).
  - Can detect 1-bit errors only.

- **LRC (Longitudinal Redundancy Check):**
  - Parity calculated across a block of data.
  - Useful for burst error detection.

- **Checksum:**
  - Sum of data segments is sent.
  - Receiver verifies sum.
  - Simple, but not very reliable for complex errors.

- **CRC (Cyclic Redundancy Check):**
  - Uses polynomial division.
  - High accuracy.
  - Used in Ethernet, 5G, and storage devices.

---

### 🧠 Deep Insight

Error detection is not about perfection — it’s about **trust with verification**. Just like human communication, we design systems to expect noise and still make sense of the message.

> “In the digital world, integrity isn’t an ideal — it’s a calculated redundancy.”

---

### 🧭 Where It’s Used

- VRC/LRC: Legacy systems and simple serial protocols
- Checksum: TCP/UDP
- CRC: Ethernet, disks, Wi-Fi

### 🔗 Links
- Previous: [LLC and Framing]({{< relref "llc-framing.md" >}})
- Next: [Error Correction and Hamming Code]({{< relref "error-correction-hamming.md" >}})
