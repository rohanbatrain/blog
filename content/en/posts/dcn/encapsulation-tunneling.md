---
date: 2025-05-12T18:06:38+05:30
title: "Encapsulation and Tunneling"
tags: ["Encapsulation", "Tunneling", "IP", "VPN", "Network Layer"]
series: "Network Layer"
categories: ["Digital Communication and Computer Networks"]
draft: false
---

### 📦 Encapsulation

Encapsulation is the process of **wrapping data** with the necessary protocol information at each layer of the OSI or TCP/IP model.

- Each layer adds a **header** (and sometimes a footer) to the data from the upper layer.
- Enables modular communication: the lower layers do not need to understand the data they are transporting.

#### 🔄 Example (Sending a Web Page over TCP/IP):

1. Application Layer: HTTP Data  
2. Transport Layer: Adds TCP Header → TCP Segment  
3. Network Layer: Adds IP Header → IP Packet  
4. Data Link Layer: Adds MAC Header/Footer → Frame  
5. Physical Layer: Converts to Bits for transmission

---

### 🕳 Tunneling

Tunneling is a method of **encapsulating packets within another protocol** to route over a network where the original protocol might not be supported.

- Enables **virtual private networks (VPNs)** and secure communication.
- Original packet is hidden inside a new one with possibly different headers.

#### 🔐 Common Use Cases:

- Sending IPv6 over an IPv4 network.
- VPNs using **IPSec, GRE, L2TP**.

---

### 🎯 Real World Example

A VPN client sends data to a VPN server. The original packet (from private IP space) is encapsulated within an outer IP packet that uses public IP addresses. At the VPN server, the outer IP header is removed, and the inner packet is forwarded as if it originated locally.

---

### 🧠 Insights

- **Encapsulation** enables layered communication and protocol independence.
- **Tunneling** enables secure or legacy-bridging communication paths across incompatible networks.
- Tunneling can add overhead but provides **security**, **routing transparency**, and **compatibility**.

---

### 🔗 Links
- Previous: [Routing Protocols: IGP & EGP]({{< relref "routing-protocols.md" >}})
- Next: [Congestion Control]({{< relref "congestion-control.md" >}})
