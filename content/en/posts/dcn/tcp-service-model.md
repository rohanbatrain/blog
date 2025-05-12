---
date: 2025-05-12T18:11:20+05:30
title: "TCP: Service Model, Protocol, and Connection Management"
tags: ["TCP", "Transport Layer", "Connection Management", "Sliding Window", "Congestion Control"]
series: "Transport Layer"
categories: ["Computer Networks"]
draft: false
---

### 🌐 Introduction to TCP

**Transmission Control Protocol (TCP)** is a **connection-oriented protocol** that provides reliable, ordered, and error-free delivery of data between applications. It ensures **data integrity**, **error recovery**, and **flow control** during data transmission.

---

### 🔄 TCP Service Model

TCP provides the following services:

1. **Reliable Data Transfer**: Guarantees the delivery of data in the correct order.
2. **Flow Control**: Prevents network congestion by adjusting the rate of data transmission.
3. **Error Detection and Recovery**: Uses checksums to detect errors and requires retransmissions in case of loss.
4. **Connection Establishment**: Three-way handshake to establish a reliable connection.
5. **Connection Release**: A formal process to terminate a connection.

---

### 🏷 TCP Segment Header

The **TCP segment header** includes:

- **Source Port**: Port number at the sender’s end.
- **Destination Port**: Port number at the receiver’s end.
- **Sequence Number**: Number assigned to the first byte of data in this segment.
- **Acknowledgment Number**: Expected sequence number for the next byte from the receiver.
- **Flags**: Control bits like SYN, ACK, FIN to manage the connection state.
- **Window Size**: Specifies the amount of data the receiver can buffer.
- **Checksum**: Ensures data integrity.

---

### 🔀 TCP Connection Establishment

1. **SYN**: The client sends a SYN packet to the server to initiate a connection.
2. **SYN-ACK**: The server responds with a SYN-ACK packet, acknowledging the client's SYN request.
3. **ACK**: The client sends an ACK packet back to the server, confirming the connection.

This three-way handshake ensures a reliable connection is established before data transfer begins.

---

### 🪢 TCP Connection Release

1. **FIN**: The sender sends a FIN packet to indicate that no more data will be transmitted.
2. **ACK**: The receiver acknowledges the FIN packet.
3. **FIN-ACK**: The receiver sends a FIN packet to the sender to close the connection.
4. **Final ACK**: The sender acknowledges the FIN packet, and the connection is closed.

---

### 🏄‍♂️ TCP Sliding Window

- **Sliding Window Protocol**: A method for controlling the flow of data between sender and receiver. It helps in managing how much data can be sent without receiving an acknowledgment.

- The **sender window** determines how many bytes can be sent before receiving an acknowledgment.
- The **receiver window** specifies the amount of available buffer space.

---

### 🌪 TCP Congestion Control

- TCP uses congestion control to prevent network overload. Techniques include:
  1. **Slow Start**: Starts by sending small amounts of data and increases gradually.
  2. **Congestion Avoidance**: Uses additive increase/multiplicative decrease (AIMD) to manage data flow.
  3. **Fast Retransmit**: Quickly retransmits packets suspected of being lost.
  4. **Fast Recovery**: Quickly recovers after packet loss by reducing the transmission rate.

---

### 🧠 Insights

- **TCP** ensures that applications can **reliably communicate** over the inherently unreliable Internet.
- The **three-way handshake** guarantees synchronization between the sender and receiver before data exchange begins.
- **Sliding window** and **congestion control** ensure that the connection adapts to network conditions, improving efficiency and avoiding congestion.

---

### 🔗 Links
- Previous: [UDP: Introduction and Remote Procedure Call (RPC)]({{< relref "udp-introduction.md" >}})
- Next: [Performance Issues and Network Performance Management]({{< relref "network-performance-management.md" >}})