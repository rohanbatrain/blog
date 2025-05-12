---
date: 2025-05-12T18:07:12+05:30
title: "Congestion Control in Networks"
tags: ["Congestion Control", "Network Performance", "QoS"]
series: "Network Layer"
categories: ["Computer Networks"]
draft: false
---

### 🚦 What is Congestion?

Congestion occurs when **too much data** is sent through the network, overwhelming routers or links, causing:

- Packet loss
- Increased delay
- Throughput degradation

It is similar to **traffic jams** on roads due to excess vehicles.

---

### 🧰 Congestion Control Techniques

1. **Open-Loop Control**
   - **Prevention-based**
   - No feedback from network
   - Techniques: Traffic shaping, admission control

2. **Closed-Loop Control**
   - **Feedback-based**
   - Monitors network to detect congestion
   - Techniques: 
     - Retransmission policies
     - Window size adjustment
     - Packet discarding strategies

---

### 📉 Indicators of Congestion

- Packet drops
- Queue build-up in routers
- Timeout-based retransmissions
- TCP slow-start triggering

---

### 📊 Algorithms & Mechanisms

- **TCP Congestion Control**
  - Slow Start
  - Congestion Avoidance
  - Fast Retransmit
  - Fast Recovery

- **Random Early Detection (RED)**
  - Proactively drops packets before the queue is full to signal congestion.

---

### 🧠 Deep Insights

- Congestion control is **not just about throughput** — it's also about **fairness** and **network health**.
- End-hosts (like TCP) and intermediate routers **cooperate** for effective control.
- Designing control algorithms requires balancing **utilization vs. delay vs. fairness**.

---

### 💡 QoS Connection

Congestion control is a **prerequisite** for achieving **Quality of Service (QoS)** — especially in real-time and multimedia communication.

---

### 🔗 Links
- Previous: [Encapsulation and Tunneling]({{< relref "encapsulation-tunneling.md" >}})
- Next: [Quality of Service]({{< relref "quality-of-service.md" >}})