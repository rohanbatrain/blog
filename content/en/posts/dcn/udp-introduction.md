---
date: 2025-05-12T18:10:41+05:30

title: "UDP: Introduction and Remote Procedure Call (RPC)"
tags: ["UDP", "Transport Protocols", "Remote Procedure Call", "Real-time Transport"]
series: "Transport Layer"
categories: ["Digital Communication and Computer Networks"]
draft: false
---

### 🌍 What is UDP?

The **User Datagram Protocol (UDP)** is a **connectionless transport layer protocol**. It provides a fast and simple communication mechanism with **no guarantees of reliability**.

- **Unreliable**: No error checking or retransmission.
- **Faster**: Lower overhead compared to TCP.
- **No Flow Control**: Applications must manage congestion and pacing.

---

### 🛠 UDP Header Format

- **Source Port**: Port number of the sending process.
- **Destination Port**: Port number of the receiving process.
- **Length**: Length of the UDP header and data.
- **Checksum**: Error-checking field (optional in IPv4, mandatory in IPv6).

---

### 💡 When to Use UDP?

UDP is ideal for applications where speed is more important than reliability, such as:

- **Voice over IP (VoIP)**
- **Streaming media**
- **DNS queries**

---

### 🧑‍💻 Remote Procedure Call (RPC)

- **RPC** allows a program to call a procedure on another address space (usually a different computer on a shared network).
- **Uses UDP** or TCP for communication, but typically UDP for speed.

**Key Steps**:
1. Client sends request to server.
2. Server processes the request and sends a response back.
3. RPC abstracts away the network communication details, making remote procedures appear local.

---

### 🚀 Real-time Transport Protocols (RTP)

- Used in applications like VoIP and streaming where **low latency** and **real-time performance** are crucial.
- Often works over UDP to minimize delay, as retransmissions (like in TCP) are not suitable for real-time applications.

---

### 🧠 Insights

- UDP sacrifices **reliability** for **speed**, making it suitable for time-sensitive applications but unsuitable for applications that require error-free data delivery.
- **RPC** is vital for distributed systems, enabling applications to call functions on remote machines as if they were local.

---

### 🔗 Links
- Previous: [Introduction to Transport Layer and Services]({{< relref "transport-layer-services.md" >}})
- Next: [TCP: Service Model, Protocol, and Connection Management]({{< relref "tcp-service-model.md" >}})
