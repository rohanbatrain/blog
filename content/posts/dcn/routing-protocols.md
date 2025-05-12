---
date: 2025-05-12T18:06:06+05:30
title: "Routing Protocols: IGP & EGP"
tags: ["IGP", "EGP", "RIP", "OSPF", "BGP", "Routing"]
series: "Network Layer"
categories: ["Computer Networks"]
draft: false
---

### 🔌 Routing Protocols: IGP and EGP

Routing protocols implement routing algorithms in real-world networks, classified based on their administrative domain:

---

### 🏠 IGP (Interior Gateway Protocol)

Used **within a single autonomous system (AS)**.

- **RIP (Routing Information Protocol)**
  - Distance-vector protocol using hop count.
  - Max hop count = 15 (limit to small networks).
  - Periodic full-table updates → bandwidth-heavy.

- **OSPF (Open Shortest Path First)**
  - Link-state protocol using Dijkstra's algorithm.
  - Each router constructs full network map.
  - Faster convergence, supports variable-length subnet masks (VLSM), and areas.

- **IS-IS (Intermediate System to Intermediate System)**
  - Similar to OSPF.
  - Scales better in large ISPs; TLV-based structure.

---

### 🌐 EGP (Exterior Gateway Protocol)

Used **between autonomous systems**.

- **BGP (Border Gateway Protocol)**
  - Path-vector protocol.
  - Considers AS-path, policy, and multiple attributes.
  - Foundation of the global internet routing.
  - Maintains table of paths; avoids loops via AS path tracking.
  - Highly scalable, supports CIDR and route aggregation.

---

### 🧠 Insights

- **IGP** optimizes for speed and simplicity inside a domain.
- **EGP** focuses on **policy-based** routing and **inter-AS stability**.
- BGP’s robustness is essential for the resilience of the internet.

---

### 📊 Comparison Table

| Feature             | IGP (e.g., RIP, OSPF)    | EGP (e.g., BGP)         |
|---------------------|---------------------------|--------------------------|
| Scope               | Within AS                 | Between ASes             |
| Convergence Speed   | Faster                    | Slower (policy checks)   |
| Complexity          | Lower                     | Higher                   |
| Policy Control      | Limited                   | Extensive                |
| Loop Avoidance      | Hop Count (RIP), Topology | AS Path                  |

---

### 🔗 Links
- Previous: [Routing Algorithms]({{< relref "routing-algorithms.md" >}})
- Next: [Encapsulation and Tunneling]({{< relref "encapsulation-tunneling.md" >}})
