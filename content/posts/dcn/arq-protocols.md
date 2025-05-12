---
date: 2025-05-12T17:54:04+05:30
title: "ARQ Protocols and Reliable Transmission"
date: 2025-05-12
tags: ["ARQ", "automatic repeat request", "reliable transmission", "data link layer", "protocols"]
series: "Data Link Layer"
categories: ["Computer Networks"]
draft: false
---

### 📡 What are ARQ Protocols?

**Automatic Repeat Request (ARQ)** protocols ensure **reliable communication** by handling the retransmission of lost or corrupted data. These protocols are widely used in **data link** and **transport layers** to ensure **integrity** and **timeliness**.

---

### 🧩 Types of ARQ Protocols

1. **Stop-and-Wait ARQ:**
   - Sender sends one frame, waits for acknowledgment (ACK).
   - **Limitation:** Low efficiency due to waiting for each frame's acknowledgment.
   - **Use Case:** Simple applications where low data rate suffices.

2. **Go-back-N ARQ:**
   - Sender sends multiple frames before needing an acknowledgment.
   - If an error occurs, all subsequent frames from the erroneous one are retransmitted.
   - **Efficiency:** Better than Stop-and-Wait, but retransmission of multiple frames can be costly.

3. **Selective Repeat ARQ:**
   - Like Go-back-N, but only the erroneous frame is retransmitted.
   - **Efficiency:** Best performance as only the lost frame is retransmitted.

---

### 🧠 Deep Insight

ARQ protocols are the digital equivalent of **reassurance** in uncertain communication. Each retransmission is not a failure, but a **validation of trust** that data will arrive as intended.

> "A protocol’s job isn’t just delivery; it’s making sure the message is received, not lost in transit."

---

### 🧭 Performance Analysis of ARQ Protocols

- **Stop-and-Wait**:
  - Simple but inefficient for high-speed communication.
  - **Throughput = Frame size / (Transmission time + RTT)**

- **Go-back-N**:
  - Throughput improves with **larger window size**, but retransmissions still impact performance.

- **Selective Repeat**:
  - **Optimal throughput** when the window size is set appropriately, offering efficient use of bandwidth with minimal retransmissions.

### 🔗 Links
- Previous: [Error Correction and Hamming Code]({{< relref "error-correction-hamming.md" >}})
- Next: [Protocols like HDLC and PPP]({{< relref "hdlc-ppp.md" >}})
