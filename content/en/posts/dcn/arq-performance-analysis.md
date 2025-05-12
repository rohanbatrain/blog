---
date: 2025-05-12T17:55:19+05:30
title: "Performance Analysis of ARQ Protocols"
tags: ["ARQ", "performance analysis", "network protocols", "data link layer"]
series: "Data Link Layer"
categories: ["Digital Communication and Computer Networks"]
draft: false
---

### 📊 Performance of ARQ Protocols

ARQ protocols are central to ensuring **reliable data transmission**, but their performance can vary based on factors like **channel quality**, **window size**, and **protocol type**. Let’s dive into the performance evaluation of **Stop-and-Wait**, **Go-back-N**, and **Selective Repeat**.

---

### 📈 Stop-and-Wait ARQ

**Efficiency:** 
- In **Stop-and-Wait ARQ**, the sender must wait for an acknowledgment after sending a frame, which leads to **poor utilization** of available bandwidth, especially in high-latency networks.

**Throughput:**
\[
\text{Throughput} = \frac{\text{Frame Size}}{\text{Transmission Time} + \text{Round-Trip Time (RTT)}}
\]
Where **RTT** represents the time for a packet to go to the receiver and back.

**Limitation:** It is highly inefficient in high-speed networks or long-distance communication, as the sender is idle for most of the round trip.

---

### ➡️ Go-back-N ARQ

**Efficiency:**
- **Go-back-N** allows sending multiple frames before receiving an acknowledgment. However, if a frame is lost or corrupted, all subsequent frames must be resent, which can cause a **reduction in efficiency**.

**Throughput:**
- **Throughput increases** as the sender can send more frames before waiting for an acknowledgment.

- **Window size** plays a crucial role here. A large window size improves performance but may also cause congestion and **out-of-order packets**.

---

### 🔄 Selective Repeat ARQ

**Efficiency:**
- **Selective Repeat** offers the highest efficiency of the three protocols. Only the **lost or corrupted frame** is retransmitted, not the entire window of frames.

**Throughput:** 
- **Selective Repeat** maximizes throughput by making **optimal use of bandwidth** and reducing the need for retransmissions.

**Window size:** A **larger window** provides better efficiency, but there are **trade-offs** in memory and complexity.

---

### 🧠 Deep Insight

The performance of ARQ protocols isn’t simply a matter of choosing one over another. It’s about **matching the protocol to the network's conditions**. The **balance between efficiency and reliability** is key to deciding which ARQ protocol to use.

> "In the world of ARQ protocols, efficiency is the dance, but reliability is the rhythm that keeps everything in sync."

---

### 🧭 Key Takeaways:

- **Stop-and-Wait** is **simple but inefficient** for high-speed or long-distance communication.
- **Go-back-N** improves throughput but introduces inefficiency due to retransmitting multiple frames.
- **Selective Repeat** offers **optimal performance** by retransmitting only the corrupted frame.

### 🔗 Links
- Previous: [HDLC and PPP Protocols]({{< relref "hdlc-ppp.md" >}})
- Next: [Error Correction and Detection Techniques]({{< relref "error-correction-detection.md" >}})
