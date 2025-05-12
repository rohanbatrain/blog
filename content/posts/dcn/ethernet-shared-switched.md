---
date: 2025-05-12T17:59:19+05:30
title: "Shared and Switched Ethernet"
tags: ["Ethernet", "shared Ethernet", "switched Ethernet", "network topologies", "performance"]
series: "Medium Access Control (MAC)"
categories: ["Computer Networks"]
draft: false
---

### 🌐 Shared Ethernet

In **Shared Ethernet**, all devices are connected to a **single broadcast medium**. This architecture typically uses **Hubs**, which transmit signals to all connected devices.

- **Channel Sharing:** Multiple devices share the same **physical medium**. If two devices attempt to transmit at the same time, **collisions** occur, causing network inefficiencies.
- **Collision Domain:** All devices within the **hub** are in the same **collision domain**, meaning they share the same **bandwidth**.
  
#### Performance Considerations:
- **Bandwidth Efficiency:** **Low** due to **collision overhead**.
- **Scalability Issues:** As more devices are added, **collision rates increase**, further reducing throughput.

#### Key Protocol: **CSMA/CD**
- Devices use **Carrier Sense Multiple Access with Collision Detection (CSMA/CD)** to avoid collisions. If a collision is detected, all devices involved **retransmit** their data after a random backoff period.

---

### ⚡ Switched Ethernet

**Switched Ethernet** uses **Ethernet switches** instead of hubs, allowing devices to communicate without the risk of collisions.

- **Point-to-Point Communication:** Each device is connected to a dedicated **switch port**, and traffic is only directed to the specific destination device.
- **Collision Domain:** Each switch port is a separate **collision domain**, meaning **no collisions** occur unless there is congestion in the network.
  
#### Performance Considerations:
- **Higher Efficiency:** No collision overhead, allowing for **higher throughput**.
- **Better Scalability:** With the use of **switches**, more devices can be added without negatively impacting network performance.

#### Key Advantage: **Dedicated Bandwidth**
- Unlike **Shared Ethernet**, each device gets **dedicated bandwidth**, leading to more predictable performance and minimal interference.

---

### 📈 Comparison: Shared vs Switched Ethernet

| Feature                | **Shared Ethernet**                     | **Switched Ethernet**                  |
|------------------------|-----------------------------------------|----------------------------------------|
| **Medium**             | Shared (Hub)                            | Dedicated (Switch)                     |
| **Collisions**         | Frequent (due to shared medium)         | Rare (due to separate collision domains)|
| **Bandwidth**          | Lower (due to contention)               | Higher (dedicated bandwidth per device)|
| **Scalability**        | Limited (increased collisions as more devices are added) | High (adding devices does not impact performance) |
| **Cost**               | Low (cheaper equipment)                | Higher (due to the cost of switches)    |

---

### 🧠 Deep Insight

**Switched Ethernet** provides significant improvements in **performance** and **scalability** over **Shared Ethernet**. With the advent of **switching technology**, the reliance on **collision avoidance** mechanisms like **CSMA/CD** has diminished, leading to more efficient use of network resources.

> "Ethernet switching has shifted the focus from merely avoiding collisions to ensuring **dedicated communication channels**, where each device can operate at its full potential."

---

### 🧭 Key Takeaways

- **Shared Ethernet** is limited by **collisions** and **bandwidth sharing**, making it less efficient as the network grows.
- **Switched Ethernet** offers **dedicated bandwidth** to devices, **eliminating collisions** and providing better scalability and higher throughput.
- Switches significantly improve **network performance** by creating separate **collision domains** for each device.

### 🔗 Links
- Previous: [Performance Analysis of MAC Protocols]({{< relref "mac-performance-analysis.md" >}})
- Next: [IEEE Standards 802.3 & 802.11]({{< relref "ieee-standards-802-3-802-11.md" >}})
