---
date: 2025-05-12T12:21:00+05:30
title: "Logical Link Control and Framing in the Data Link Layer"
tags: ["data link layer", "LLC", "framing", "networking", "protocols"]
series: "Data Link Layer"
categories: ["Digital Communication and Computer Networks"]
draft: false
---

### 📚 What is LLC?

The **Logical Link Control (LLC)** is the upper sublayer of the Data Link Layer. It manages:
- Framing
- Error checking
- Flow control
- Interface to the Network Layer

LLC is defined in **IEEE 802.2** and is common across many IEEE LAN standards (like Ethernet, Wi-Fi).

---

### 🧱 Framing

Framing is the process of encapsulating data with control information so that it can be transmitted over the physical medium. Each **frame** includes:
- **Header:** Contains addressing and control info
- **Payload:** Actual data from the Network Layer
- **Trailer:** Often includes error-checking bits (e.g., CRC)

---

### 🧠 Deep Insight

Framing is how **order emerges from chaos** on the wire. Without it, streams of bits have no structure or meaning. LLC and framing define **the grammar of digital communication**.

> “A frame is more than data — it's context, identity, and integrity in motion.”

---

### 🧭 Types of Framing

- **Byte-oriented:** Uses special characters (PPP)
- **Bit-oriented:** Uses bit patterns with bit stuffing (HDLC)
- **Clock-based:** Uses timing info (rare in LLC)

### 🔗 Links
- Next: [Character Encoding and Error Detection]({{< relref "error-correction-detection.md" >}})
- Related: [Communication Channels and Performance]({{< relref "comm-channels-performance.md" >}})
