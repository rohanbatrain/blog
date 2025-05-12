---
date: 2025-05-12T18:04:08+05:30
title: "Routing Algorithms"
tags: ["Routing", "Distance Vector", "Link State", "Dijkstra", "Bellman-Ford"]
series: "Network Layer"
categories: ["Computer Networks"]
draft: false
---

### 🧭 Routing Algorithms

Routing algorithms are essential to determine the best path for data to travel across networks. They fall into two broad categories: **Distance-Vector** and **Link-State**.

---

### 📌 1. Distance Vector Routing

Each router maintains a table (vector) that holds the best-known distance to every destination.

- Based on **Bellman-Ford Algorithm**
- Routers exchange vectors with neighbors periodically.
- Simple but slow convergence; prone to **count-to-infinity** problems.

**Example Protocol**: RIP (Routing Information Protocol)

---

### 🛣 2. Link-State Routing

Each router has a complete view of the network topology and calculates the shortest path using **Dijkstra’s Algorithm**.

- Routers send **Link State Advertisements (LSAs)**.
- Builds a **link-state database** and a **shortest-path tree**.
- Faster convergence and better scalability.

**Example Protocol**: OSPF (Open Shortest Path First)

---

### 🔍 Key Routing Algorithms

#### 🧮 Bellman-Ford Algorithm (Distance Vector)

- Each node maintains a table of distances.
- Repeatedly updates table entries based on neighbor's info.
- Can handle **negative weights**, but slow convergence.

#### 📐 Dijkstra's Algorithm (Link State)

- Calculates shortest paths from a source node.
- Uses a priority queue (min-heap) for efficiency.
- Requires knowledge of the **entire network**.

---

### 📊 Comparison

| Feature                  | Distance Vector (Bellman-Ford) | Link State (Dijkstra) |
|--------------------------|-------------------------------|------------------------|
| Network Knowledge        | Local (neighbors only)         | Global (entire network)|
| Convergence Speed        | Slow                           | Fast                   |
| Scalability              | Less scalable                  | More scalable          |
| Algorithm Used           | Bellman-Ford                   | Dijkstra               |
| Example Protocol         | RIP                            | OSPF                   |

---

### 💡 Deep Insights

- Routing efficiency is a trade-off between **knowledge** and **overhead**.
- Distance Vector is lightweight but less responsive to changes.
- Link-State requires more resources but enables **faster and smarter** decisions.

---

### 🔗 Links
- Previous: [Network-Layer Protocols]({{< relref "network-layer-protocols.md" >}})
- Next: [Routing Protocols: IGP & EGP]({{< relref "routing-protocols.md" >}})
