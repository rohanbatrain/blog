---
date: 2025-05-12T18:07:38+05:30
title: "Quality of Service (QoS) in Networking"
tags: ["QoS", "Bandwidth", "Delay", "Jitter", "Packet Loss"]
series: "Network Layer"
categories: ["Digital Communication and Computer Networks"]
draft: false
---

### 🌟 What is Quality of Service (QoS)?

QoS refers to a network’s ability to **provide predictable service quality** — essential for real-time and critical applications (VoIP, video streaming, online gaming).

It focuses on **managing network resources** to meet performance requirements.

---

### 📏 Key QoS Metrics

1. **Bandwidth** – Data transfer capacity of the network.
2. **Delay (Latency)** – Time for a packet to reach the destination.
3. **Jitter** – Variation in delay; critical for media quality.
4. **Packet Loss** – Percentage of packets that fail to reach destination.

---

### 🛠 Mechanisms to Ensure QoS

- **Traffic Classification and Prioritization**
  - Differentiated Services (DiffServ)
  - Integrated Services (IntServ)

- **Traffic Shaping**
  - Regulates flow to reduce bursts (e.g., token bucket, leaky bucket).

- **Resource Reservation**
  - RSVP (Resource Reservation Protocol) in IntServ architecture.

- **Queuing Disciplines**
  - FIFO, Priority Queuing, Weighted Fair Queuing (WFQ)

---

### 💡 Real-world Example

In a video call:
- **Bandwidth** ensures smooth visuals.
- **Low delay** ensures no lag.
- **Low jitter** ensures voice/video sync.
- **No packet loss** ensures quality and intelligibility.

---

### 🧠 Insights

- QoS turns “best-effort” networks into **deterministic performance zones**.
- Vital for enterprise networks, ISPs, and any delay-sensitive service.
- Proper congestion control **enables QoS**; they are tightly coupled.

---

### 🧪 Wireshark Tip

Use Wireshark to monitor:
- Delay variation
- Packet reorderings
- DSCP field in IP header (used in DiffServ QoS)

---

### 🔗 Links
- Previous: [Congestion Control]({{< relref "congestion-control.md" >}})
- Next: [Wireshark Introduction]({{< relref "wireshark-tool.md" >}})
